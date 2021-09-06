---
title: "Setting up JupyterLab"
teaching: 0
exercises: 0
questions:
- "What is JupyterLab?"
- "How do I setup JupyterLab on COLA computers?"
objectives:
- "Explain what JupyterLab is and why we are using it"
- "Explain how to setup JupyterLab on COLA servers"
- "Explain what you can do with JupyterLab"
keypoints:
- "JupyterLab is an interactive Python interface that is ideal for scientific work"
- "Launching JupyterLab is a multi-step process"
- "Launch the server on a COLA computer `jupyter lab --no-browser --ip=`hostname` --port=8878`"
- "Login to COLA computer with special login line: `ssh -N -L 8878:colaX.gmu.edu:8878 YOURUSERNAME@colaX.gmu.edu`"
- "Open JupyterLab in your web browser: http://localhost:8878" 
---
## Why do we need to setup another program? 

We have been using the Unix command line to type and execute our Python commands.  This is not a nice interface for working, especially as our codes get larger.
We will use a browser-based interface called `JupyterLab` or `Jupyter notebook`. Jupyter notebooks are also ideal for scientific research because they make it easy to document our work, include equations in our documentation, show our analysis results, and link to other resources like journal articles. 
Let's set it up and see what it can do!

## Setup JupyterLab on COLA Computers

#### 1. Login to a COLA computer (X refers to the computer number)

~~~
$ ssh -Y -l YOURUSERNAME colaX.gmu.edu
~~~
{: .language-bash}


#### 2. Load the anaconda module
~~~
$ module load anaconda/3
~~~
{: .language-bash}

#### 3. Setup a password for Jupyter.  This will be different from your COLA or Mason passwords.

~~~
$ jupyter notebook --generate-config
$ jupyter notebook password
~~~
{: .language-bash}

#### 4. Start the Jupyter server with the following command (which asks for port 8878)

~~~
$ jupyter lab --no-browser --ip=`hostname` --port=8878
~~~
{: .language-bash}

> ## Pay attention here, if port 8878 is busy you might automatically get assigned a different port
> For example: 
> ~~~
>[I 19:01:58.026 LabApp] The Jupyter Notebook is running at:
>[I 19:01:58.026 LabApp] http://cola1.gmu.edu:8879/
> ~~~
{: .callout}

#### 5. In a separate XQuartz or MobusXterm window, log into the <u>same</u> cola machine (colaX) again with the following command

~~~
$ ssh -N -L 8878:colaX.gmu.edu:8878 YOURUSERNAME@colaX.gmu.edu
~~~
{: .language-bash}
Nothing will happen after you type your password

> ## Again pay attention!
> Make sure that in steps 4 and 5 same cola machine and port is being used.
{: .callout}

#### 6. Open a web browser and go to  http://localhost:8878. It will ask you to enter the password you created in step 1.
Jupyter will appear in your local browser

> ## What can go wrong here?
>
> There are various errors that can happen that will not allow the Jupyter to launch properly:
>
> ~~~
> Traceback (most recent call last): File “/homes/sknapp4/.conda/envs/aoes/lib/python3.6/site-packages/traitlets/traitlets.py”, line 528, in get value = obj._trait_values[self.name] KeyError: ‘allow_remote_access’
> ~~~
> {: .error}
>
> Solution: Try launching Jupyter with the following command
>
> ~~~
> $ jupyter lab –no-browser –ip=’0.0.0.0’ –port=8878
> ~~~
>
> If you get an Invalid Credentials error, check the messages on the screen where you launched `jupyter lab ` Sometimes port 8878 is in use and it will find a different port. The error messages will tell you which port you should use.
>
> These errors messages look like:
> ~~~
jupyter lab –no-browser –ip=`hostname` –port=8878 [I 14:12:20.887 LabApp] The port 8878 is already in use, trying another port.
> ~~~
> {: .language-bash}
>
> Solution: Repeat step 6 using the reccomended port.
>
{: .callout}


#### 8. In the upper right corner, you will see your current environment. 
You may have others but we will start by using the default "Python 3" environment.

## What do I do now that JupyterLab is setup?

Now that you have completed the setup process, you need to execute steps 5,6,and 7 when you want to run JupyterLab.

> ## Test that you can login and launch JupyterLab
>
>  Logout of COLA computers.  Login again and launch JupyterLab
>
{: .challenge}