# Project Environment for VT-CS Compilers Course

This is the dockerfile repository for the project environment of VT-CS Compilers Course.

All project grading will be done within this environment.

## Environment

- Environment is based on `debian:stable`
- JDK is OpenJDK 17 from Debian repository
- Python is Python 3.11.2 from Debian repository
- Antlr 4.9.1 Complete Jar Ball is installed at `/usr/local/share/antlr.jar`
- Python 3.11.2 runtime for Antlr 4.9.1 is installed from Debian repository
- A convenient script to call Antlr tool is installed at `/usr/local/bin/antlr` and calling `antlr` would invoke it
- `CLASSPATH` environment variable is set to the above jar ball so all Java program depending on Antlr runtime shall run without problem.
- [RiscSim](https://github.com/kirshanthans/RiscSim) will be cloned at `/home/user/RiscSim`
- `sudo` is available to use without password, in case you need any system-level modifications

## Usage

In a docker installation,

```(bash)
docker pull ghcr.io/cs-vtcompilers/env-container:latest
```

and run it with

```(bash)
docker run -it ghcr.io/cs-vtcompilers/env-container:latest
```

to get a command line running in the environment.

A very typical set of flags would be giving the container a name, also using volumes to map your project folder from the container host into the container:

```(bash)
docker run -it --name compiler_project -v /path/to/project/repo/folder:/home/user/repo ghcr.io/cs-vtcompilers/env-container
```

And with a name, after exiting the container, it could be later re-started with:

```(bash)
docker start -ia compiler_project
```