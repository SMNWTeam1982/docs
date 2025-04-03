# Package Management with Pipenv

The chosen package manager for Team 1982 programming is `pipenv`, as we explained in [philosophy/On Package Management](/docs/philosophy/on-package-management). This page documents the usage, nuances and applications of `pipenv` as it's used with our FRC code.

## Setting up Pipenv
As our projects depend on Pipenv for local dependency management on development machines, it must be installed system-wide to be used effectively. Although the setup instructions are detailed on the pipenv documentation, the district-provided machines can be tricky to work with. View the below guides for your system, assuming a MacOS device is school provided.

<details>
  <summary>Windows Setup</summary>
  The Team 1982 programming computers are already properly configured for use with <code>pipenv</code>, but in the event that you want to use a personal device or need to reprovision the programming computers for any reason, the following guide should work.
  <h4>Install Python</h4>
  RobotPy requires a modern version of Python to function, as does pipenv. If you do not already have Python <code>>=3.12</code> installed on your system, you may skip this step. If you need to install Python on your system, first open <a href="https://python.org/downloads">the Python download page</a> and download te most recent version of Python 3.12 and follow through the installation steps. When installing, ensure the following boxes are checked if you reach an 'Optional Features' screen. (If you do not see this, look for an 'Advanced' or 'Customize installation' button.)
  <img src="/docs/images/python-installer-options.png">
  Also ensure that an option for 'Add python.exe to path' is checked as it will make life easier down the line. Beyond this, the installation should be successful and you can move on to installing pipenv itself.
  <h4>Installing Pipenv</h4>
  Although not recommended, we make use of a system-wide installation of pipenv for managing our dependencies, meaning that you must ask pip to break system packages during the install. This sounds more scary than it is, as we will not be using the system pip install anymore. Open a powershell prompt and run 
  <br>
  <code>python -m pip install --break-system-packages pipenv</code>
  <br>
  Which should fully install pipenv system-wide, and make it available from any command prompt (e.g. VSCode, Powershell, Windows Terminal).
  Now that pipenv is installed, you can move on to usage instructions.
</details>
<br>
<details>
  <summary>MacOS Setup</summary>
  Our goal is to make development as accessible as possible for our team's programmers, and as such, allow them to program on their district provided devices from anywhere. The district provided MacBook's are locked down to some extent, so there are some additional steps to take when installing.
  <h4>Installing Homebrew</h4>
  Although not necessary, installing Homebrew vastly improves the user experience of managing software on MacOS. The district provided MacBooks cannot install Homebrew per the traditional method, and must be installed manually. For more information on this, as well as a script to automate this process, see <a href="https://github.com/FloridaMan7588/brewhax">FloridaMan7588/Brewhax (WIP)</a>. On non-managed systems, Homebrew can be installed by running the following in a terminal: 
  <br>
  <code>/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"</code><sup><a href="#references">1^</a></sup>
  <br>
  <br>
  After Homebrew has been installed, you can move on to Installing Python.

  <h4>Installing Python</h4>
  Brew vastly simplifies the installation of Python and Pipenv, which can be done by simply running
  <br>
  <code>brew install python@3.12 pipenv</code>
  <br>
  This installs all of the required dependencies for both Python and Pipenv. Beware that on system's with non-standard Homebrew install locations (e.g. using the script above), this may take a long time as several large packages have to compile. On M1 systems this may only take a few minutes.
</details>
<br>
<details>
  <summary>Linux Setup</summary>
  Although we do not use Linux on our primary machines, you may still want to at home or on one of the slower computers. In the case that you need to install Python or Pipenv, this varies by Distribution, but generally the packages follow the pattern of <code>python3 python3-pipenv</code> or some variation of that. On Ubuntu, for example, you can install both with <code>sudo apt install python pipenv</code>. From here, you can move on to usage instructions.
</details>
<br>
For more information on the tooling we make use of, see <a href="/docs/programming/tools">programming/Tooling</a> for setup instructions and usage information.

## Managing Software Dependencies
The `pipenv` command is used in tandem with the `Pipfile` and `Pipfile.lock` to manage the installed dependencies within the virtual environment that pipenv manages. 

### Installing Dependencies
For managing what is installed in the development environment, `pipenv install` is provided to add packages and install existing packages specified in the Pipfile and lockfile. When adding dependencies to the project, they can either be added as development dependencies or as Robotpy dependencies. For development dependencies, they only need to be added to the Pipfile, which is done automatically when running `pipenv install`. Dependencies that need to be installed on the robot (Robotpy dependencies) must also be added to the `pyproject.toml` file, which can be done manually by editing the file.

### Removing Dependencies
If the project no longer depends on a library, you can remove it from the project file with `pipenv uninstall [package]`, although it may still be present in the `pyproject.toml` and will thus be installed on the RoboRIO as well. If you wish to prevent installation on the RIO as well, remove the package from the pyproject file.

## Scripting
Pipenv also supports scripts within the Pipfile, making it easy to execute repetitive commands without having to type them. By default, our [swerve-template](https://github.com/smnwteam1982/swerve-template) repository includes a Pipfile which has 4 commands predefined:
- `pipenv run sync`
- `pipenv run deploy`
- `pipenv run sim`
- `pipenv run test`

These commands simplify the deploying of code to the robot and management of Robotpy dependencies.

#### `pipenv run sync`
The Sync command downloads the dependencies required for the RoboRIO to function, and must be re-run every time there is an update to `pyproject.toml`. The Sync command also prompts for updating dependencies, which should usually be ignored as this is managed by `pipenv`

#### `pipenv run deploy`
The Deploy command does exactly as it says, deploys the code to a connected RoboRIO. This command is platform agnostic, but the FRC Driver Station does not run on non-Windows platforms, so test with care.

#### `pipenv run sim`
The Sim command creates a realtime simulation of the Robot, although this is not fully supported and our code does not implement many of the sim features.

#### `pipenv run test`
The Test command runs the `pyfrc` test suite on the project to validate everything is setup correctly, and that the robot code will deploy withot errors. This is also automatically run on deploy.



## References
1. [Homebrew installation page](https://brew.sh)