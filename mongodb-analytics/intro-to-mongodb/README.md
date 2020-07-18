# Mongodb intro course

### Altas (mongo cloud) account

https://account.mongodb.com/account/login

### Downloading Mongo db

Google it, just don't click on the add.  Also, weirdly, it doesn't seem like the installation includes updating the system path, so you have to do that manually.

```
mongo "mongodb+srv://cluster0.wzlug.mongodb.net/coursera1" --username admin
```

### Getting first data into Mongodb

I already loaded a bunch of sample data, so need to make sure I am careful about how I name stuff, etc.

created a db/namespace (?) called `coursera1` and a collection called `movies_initial`.

***Note: looks like the Atlas web interface has changed since the course was created***
***As of 2020-07-18***

Where I found documentation on `mongoimport`:
 - https://docs.atlas.mongodb.com/command-line-tools/#connect-with-mongoimport

```
mongoimport --host atlas-hndvh0-shard-0/cluster0-shard-00-00.wzlug.mongodb.net:27017,cluster0-shard-00-01.wzlug.mongodb.net:27017,cluster0-shard-00-02.wzlug.mongodb.net:27017 --ssl --username admin --password r7hgth4PonRH5TQG --authenticationDatabase admin --db coursera1 --collection movies_initial --type CSV --file movies_initial.csv
```

note though, have to add the `--headerline` parameter to the command above.

### Python and PyMongo

See the week 1 scratch notebook `./week1_scratch`.

### Setting up the environment

Skipped over this earlier, but coming back to it.

First open the anaconda prompt and navigate to:

```
C:\Users\dan\Desktop\git_repos\coursera\mongodb-analytics\intro-to-mongodb
```

Then create the environment... Before I do this though, want to do a [little research](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#creating-an-environment-with-commands) on what's going on with the command below.

Basically it is telling conda to create an environment called `intro-to-mongodb` but without doing anything with it, I think it just creates a folder in the `envs` folder within the anaconda directory.

```
conda create -n intro-to-mongodb
```

Let's see what is in there (if anything).  

```
conda list -n intro-to-mongodb
```

Nothing, how about this:

```
(base) C:\Users\dan\Desktop\git_repos\coursera\mongodb-analytics\intro-to-mongodb>conda env list
# conda environments:
#
base                  *  C:\ProgramData\Anaconda3
intro-to-mongodb         C:\Users\dan\.conda\envs\intro-to-mongodb
```

```
conda list -n base
```

Yeah, that basically has everything in it.  So I basically have an empty environment?

Well, let's activate it and see what's up:

```
activate intro-to-mongodb
```

Yeah, wild, apparently this thing is totally empty:

```
(intro-to-mongodb) C:\Users\dan\Desktop\git_repos\coursera\mongodb-analytics\intro-to-mongodb>conda list
# packages in environment at C:\Users\dan\.conda\envs\intro-to-mongodb:
#
# Name                    Version                   Build  Channel

(intro-to-mongodb) C:\Users\dan\Desktop\git_repos\coursera\mongodb-analytics\intro-to-mongodb>
```

Well, ok, whatever, let's keep following the coursera "setting up your environment" instructions and see where this goes.

OK, either I did something wrong, or these are terrible instructions.  I create an empty environment, and then am told to run the `jupyter notebook` command, and in the empty environment, the machine has no idea whay jupyter is.

So what to do now?  I can either put everything I need in the base envirnoment, or figure out how to copy my existing base envirnoment (which is whatever the anaconda default is as of 2020-07-18, plus `pymongo` and `dnspython`).

Let's see if we can actually make the new environment work (based on same link from above, just ctrl-f "clone")

```
(base) C:\Users\dan\Desktop\git_repos\coursera\mongodb-analytics\intro-to-mongodb\notebooks>conda create --name intro-to-mongodb  --clone base
WARNING: A conda environment already exists at 'C:\Users\dan\.conda\envs\intro-to-mongodb'
Remove existing environment (y/[n])? y

Source:      C:\ProgramData\Anaconda3
Destination: C:\Users\dan\.conda\envs\intro-to-mongodb
The following packages cannot be cloned out of the root environment:
 - defaults/win-64::conda-4.8.3-py37_0
 - defaults/win-64::conda-build-3.18.11-py37_0
 - defaults/win-64::conda-env-2.6.0-1
Packages: 299
Files: 11
Preparing transaction: done
Verifying transaction: done
Executing transaction: - DEBUG menuinst_win32:__init__(199): Menu: name: 'Anaconda${PY_VER} ${PLATFORM}', prefix: 'C:\Users\dan\.conda\envs\intro-to-mongodb', env_name: 'intro-to-mongodb', mode: 'user', used_mode: 'user'
DEBUG menuinst_win32:create(323): Shortcut cmd is %windir%\System32\cmd.exe, args are ['"/K"', 'C:\\ProgramData\\Anaconda3\\Scripts\\activate.bat', 'C:\\Users\\dan\\.conda\\envs\\intro-to-mongodb']
- DEBUG menuinst_win32:__init__(199): Menu: name: 'Anaconda${PY_VER} ${PLATFORM}', prefix: 'C:\Users\dan\.conda\envs\intro-to-mongodb', env_name: 'intro-to-mongodb', mode: 'user', used_mode: 'user'
DEBUG menuinst_win32:create(323): Shortcut cmd is %windir%\System32\WindowsPowerShell\v1.0\powershell.exe, args are ['-ExecutionPolicy', 'ByPass', '-NoExit', '-Command', '"& \'C:\\ProgramData\\Anaconda3\\shell\\condabin\\conda-hook.ps1\' ; conda activate \'C:\\Users\\dan\\.conda\\envs\\intro-to-mongodb\' "']
/ DEBUG menuinst_win32:__init__(199): Menu: name: 'Anaconda${PY_VER} ${PLATFORM}', prefix: 'C:\Users\dan\.conda\envs\intro-to-mongodb', env_name: 'intro-to-mongodb', mode: 'user', used_mode: 'user'
DEBUG menuinst_win32:create(323): Shortcut cmd is C:\ProgramData\Anaconda3\python.exe, args are ['C:\\ProgramData\\Anaconda3\\cwp.py', 'C:\\Users\\dan\\.conda\\envs\\intro-to-mongodb', 'C:\\Users\\dan\\.conda\\envs\\intro-to-mongodb\\python.exe', 'C:\\Users\\dan\\.conda\\envs\\intro-to-mongodb\\Scripts\\jupyter-notebook-script.py', '"%USERPROFILE%/"']
done
#
# To activate this environment, use
#
#     $ conda activate intro-to-mongodb
#
# To deactivate an active environment, use
#
#     $ conda deactivate
```
***shit, I think this is literally copying over everything from base, which I suppose I should have realized.  Ok, well, maybe I will keep it, I wonder if it means I will also have a separate version of spyder for this environment.***



***bah, also on my to do list is to find something equivalent to tmux, or something to allow jupyter to run in the background and not tie up my shell***





conda create -n intro-to-mongodb
