There are many repositories out there to provide vulnerable environments such as web applications, containers or virtual machines, since it helps not only students or someone who recently joined the field to learn the relevant techs, but also security professionals to keep hand-on.

Among the approaches, the easiest way these days is using containers(e.g. docker or podman).

Running containers with like just one command such as `docker run` or `docker compose up` sounds awesome!

### Problem statement

The problem is, you cannot exactly know what it does(especially, considering it is a **vulnerable** container), when running a container, if you simply run a container without knowing how it was built.

Dockerfile provides the information.

Although sometimes Dockerfile is available in the registry service such as [hub.docker.com](http://hub.docker.com) or [quay.io](https://quay.io) or some information on what commands have been used can be derived from `docker history` or IMAGE LAYERS is available, it is challenging to find out some important information such as the base image which was used to build the image (e.g. specified as FROM  in Dockerfile)

What’s a risker situation is, when a user is asked to run docker with the `-v` option or docker-compose whose config file has volume configuration. If they do not pay attention, a possible scenario may include where their files on the host can be stolen to some malicious users.  If a user is asked to run a container with `--privileged` or `--user=root`, it can be much more serious, as there is a risk where an attacker can set a foothold in the container and escape to your host.

See [Docker Security - OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/cheatsheets/Docker_Security_Cheat_Sheet.html) for more information on Docker security.

Therefore, a User who wants to learn or set up test environments must be cautious when running a vulnerable container image. Providing the user with the access to Dockerfile and documentation will help minimize such risks, if not all, so that the user can enjoy learning and practicing for security safely.

### VULCONHUB

The OWASP Vulnerable Container Hub(VULCONHUB) is a project that provides:

- access to Dockerfile(or a similar Containerfile) along with files that are used to build the vulnerable container image
- documentation such as README that describes how to use the container, and optionally, a link to the image in the registry service such as Docker Hub or Quay.io, where a user can directly pull and run the container (on their own account).

The files provided in the repository allow users to build vulnerable container images, so that they can freely and **safely** learn, play, practice, and perform quick proof-of-concepts of CVE vulnerabilities or use them for preparation for their CTF challenges.

The ultimate goal of the project is to become the go-to reference to help anyone interested in security to share and maintain such useful container build files for security learning and practices.


### Usage

1. Init and update submodules (a submodule is a link to the original repository). 

```bash
$ git submodule init
$ git submodule update
```

It is also possible to specify a path which is only necessary for you, to reduce time and keep disk usage to a minimum.

```bash
$ git submodule init <path> [--recursive]
```
For more information on the git submodule, see [https://git-scm.com/book/en/v2/Git-Tools-Submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules).

2. cd to a directory you are interested in.
3. Examine Dockerfile
4. Build your own container image

`$ docker build . -t local/<image-name>`

5. Run with the proper option such as port. See documentation such as README available in the directory.

```bash
$ docker run -p <hostport>:<containerport> local/<image-name>
```

# Contributing

Any contribution is more than welcome!!

Please create a Pull Request to add new container build files. Either adding your own files or adding submodules will be welcome.

For a pull request to be merged, each directory must have the following:

1. Dockerfile and necessary files to build a vulnerable container
2. README to describe how to run and use the container.


