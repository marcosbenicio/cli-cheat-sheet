# **Outline**

- [**Shell Commands**](#shell-commands)
    - [**Bash**](#bash)
    - [**SSH**](#ssh)
- [**Line-Commands Tools**](#line-commands-tools)
    - [**Git/GitHub**](#gitgithub)
        - [**Config and Init**](#config-and-init)
        - [**Branch and Checkout**](#branch-and-checkout)
        - [**Stage area and commit**](#stage-area-and-commit)
        - [**Remote**](#remote)
        - [**Push and Pull**](#push-and-pull)
        - [**Merge and Rebase**](#merge-and-rebase)
        - [**Large Files**](#large-files)
    - [**Pipenv**](#pipenv)
    - [**Docker**](#docker)
    - [**Kubernetes and Kind**](#kubernetes-and-kind)
    - [**Others**](#others)
        - [**Repository structure**](#repository-structure)
        - [**jupyter**](#jupyter)
        - [**Jekyll**](#jekyll)
        - [**Xelatex**](#xelatex)

# Shell commands

# **Bash**

Copy the file to the destination repository:

```bash
cp /path/to/source/repo/file /path/to/destination/repo/
```

Rename a file in a repository:

```bash
mv old-file-name <new-file-name >
```

Remove all files and subdirectories in the current directory:

```bash
rm -rf *
```

Find the location of a program:

```bash
which <program-name >
```
Return the type of a program:

```bash
type <program-name >
```

List all the files installed by a program. The `dpkg` is the package management program that installs, removes, and provides information about `.deb` packages. The `grep` command-line searches through text and prints lines that match a pattern.

```bash
dpkg -L <program-name > | grep bin/
```


netstat is a command-line utility that displays network connections for the Transmission Control Protocol (both incoming and outgoing), routing tables, and a number of network interface (network interface controller or software-defined network interface) and network protocol statistics. The `t` flag is used to display TCP connections, the `u` flag is used to display UDP connections, the `l` flag is used to display only listening sockets, and the `n` flag is used to display numerical addresses instead of trying to determine symbolic host, port or user names. `grep <port-number>` is used to filter the displayed connections by a specific port number.

```bash
netstat -tuln | grep <port-number >
```

`lsof` stands for "list open files". Display information about files opened by processes. The `i` flag is used to display only internet connections, the `p` flag is used to display the PID and name of the program to which each socket belongs, and the `n` flag is used to display numerical addresses instead of trying to determine symbolic host, port or user names.

```bash
lsof -i -P -n | grep <port-number >
```

```bash
sudo lsof -i :9696
```

A cross-platform command-line utility that creates projects from cookiecutters (project templates):


------

# **SSH**

cluster access (Password: marcos0102)
   
```bash
ssh -Y mbenicio@146.164.45.180 -p  20022
```
CHange password:

```bash
passwd 
```

A "node" refers to a single computer or machine within the cluster. Each node can be a separate physical server, or it can be a virtual machine. To change of node in a cluster use:

```bash
ssh cn025
```

List all the nodes in the cluster:

```bash
sinfo -l
```

Displays information about the CPU architecture:

```bash
lscpu
```

Shows the amount of free and used memory in the system .
```bash
free -h
```

Information about the disk space usage on the cluster:
```bash
df -h
```

Gives detailed information about the GPU NVIDIA models, usage, memory:

```bash
nvidia-smi
```

Displays basic information about the system's kernel, operating system, and hardware platform:

```bash
uname -a
```

Commands show the current usage of CPU, memory, and other resources in real-time

```bash
top
```
or  more user-friendly interface:

```bash
htop
```

# **Line-Commands Tools**

------

# **Git/GitHub**

## **config and init**

List all the git configurations:

```bash
git config --list

git config --global --list

git config --local --list

```

Set the default branch name to main as in GitHub:

```bash
git config --global init.defaultBranch main
```

Initialize a git repository:

```bash
git init
```

Establish a new remote repository that our local repository can interact with:

```bash
git remote add origin <SSH_URL or HTTPS >
```

Difference between the working directory and the staging area:

```bash
git diff
```

List of news files and modified files:

```bash
git status
```

## **branch and checkout**

**git branch** is used for creating, listing, and deleting branches, while **git checkout** is used for switching between branches and also for creating a new branch if used with the -b flag.


List all the branches in the repository with -a flag:

```bash
git branch -a
```
or delete a branch with -d (-D to force deletion) flag:

```bash
git branch -d <branch-name>
```

Create and immediately switch to a new branch:

```bash
git branch -b <new-branch-name >
```
or

```bash
git checkout <new-branch-name >
```

Switch to an existing branch:

```bash
git checkout <branch-name >
```

Rename a branch:

```bash
git branch -m <old-branch-name> <new-branch-name>
```

## **Stage area and commit**

</center> <img src="git.png" alt="drawing" width="1000" /> </center>


Add a file to the staging area:

```bash
git add <file-name >
```

Remove a file from the staging area before commit:

```bash
git reset <file-name >
```

Commit changes to head:

```bash
git commit -m "Commit message"
```

Stop tracking a file that was previously committed to the repository.  It's often used for files that should no longer be part of the repository (e.g., accidentally committed files, files that should be ignored).

```bash
git rm --cached <file-name>
```

Or remove all files from the staging area.The -r flag is for recursive removal, and . indicates the current directory.

```bash
git rm --cached -r .
```


Change the commit message or add/untrack  files to last commit (only if not pushed and after staging/unstaging the files with `git add` / `git rm`):

```bash
git commit --amend -m "New commit message"
```

Show the commit history for the currently active branch:

```bash
git log
```

## **Push and Pull**

Push the branch to remote repository:

```bash
git push origin <branch-name >
```

Pull changes from the remote repository to the local repository:

```bash
git pull origin <branch-name >
```

Fetch the changes from the remote repository to the local repository:

```bash
git fetch origin <branch-name >
```

## **Merge and Rebase**

Merge the specified branch into the current branch:

```bash
git merge <branch-name >
```

Rebase the current HEAD onto the specified branch:

```bash
git rebase <branch-name >
```

Create a new commit that undoes all of the changes made in <commit-hash >, then apply it to the current branch:

```bash
git revert <commit-hash >
```

## **Remote**

Replace the current working directory and staging area with the state of the tree at the given commit:

```bash
git reset --hard [commit-hash]

```

If we only want to reset the staging area and not affect the working directory. This will unstage any changes since the specified commit, but leave the files in the working directory unchanged. 

```bash
git reset [commit-hash]
```

Switch a repository's remote URL to use SSH in GitHub:

```bash
git remote set-url origin <SSH_URL >
```

List all the remote repositories:

```bash
git remote -v
```

## Large Files

initializes Git LFS in repository:

```bash
git lfs install
```

Track a file with Git LFS. It adds entries to the `.gitattributes`.

```bash
git lfs track <file-name >
```

Untrack a file with Git LFS:

```bash
git lfs untrack <file-name >
```

List all the files tracked by Git LFS:

```bash
git lfs ls-files
```

------
# **Pipenv**


Install Pipenv to manage project dependencies.

```bash
pip install pipenv
```
Install a specific package and add it to Pipfile.

```bash
pipenv install <package-name >
```


Uninstall a specific package and remove it from Pipfile.

```bash
pipenv uninstall <package-name >
```

Activate the virtual environment associated with your project.

```bash
pipenv bash
```

Remove the virtual environment for the project.

```bash
pipenv --rm
```

Update all packages to their latest versions as specified in Pipfile.

```bash
pipenv update
```

Update a specific package to its latest version as specified in Pipfile.

```bash
pipenv lock
```

Exit the virtual environment:

```bash
exit
```
------
# **Docker**


Download docker image:

```bash
sudo docker pull <docker-image >
```

List of docker images:

```bash
sudo docker images
```

Run docker image. The flags `-it`, it allows to interact with a command line interface within the Docker container.  the `--rm` flag automatically removes the container when it exits and `.` specifies the build context to the current directory.

```bash
sudo docker run -it --rm -p 9696:9696 <docker-image >:tag .
```


List all containers (running and stopped). `ps` is used to list running process on unix and
`-a` stands for 'all' process.

```bash
sudo docker ps -a
```

Inspect a docker object:

```bash
sudo docker inspect <image_or_container_id >
```

Remove a docker container forcefully:

```bash
sudo docker rm -f <container_id >
```

Remove a docker image forcefully:

```bash
sudo docker rmi -f <image_id >
```

Remove all stopped containers, not tagged images, and unused networks and volumes.

```bash
docker system prune -a
```
------
# **Kubernetes and Kind**


Create a cluster with `kind`:

```bash
kind create cluster
```

Check with `kubectl` that it was successfully created:

```bash
kubectl cluster-info
```

Load a docker image into the cluster:

```bash
kind load docker-image
```

Apply configuration to our cluster from a YAML file. The `-f` flag specifies the filename. 

```bash
kubectl apply -f <filename >.yaml
```

Delete the Kubernetes resources defined in a given YAML file from our cluster:

```bash
sudo kubectl delete -f <filename >.yaml
```

List all deployments:

```bash
kubectl get deployments
```

Delete a deployment:

```bash
kubectl delete deployment <deployment-name >
```

List all pods:

```bash
kubectl get pods
```

List all services:

```bash
kubectl get services
```

Delete a service:
```bash
kubectl delete service <service-name >
```

Create the HPA (Horizontal Pod Autoscaler) for the deployment:

```bash
kubectl autoscale deployment <label-name-pod > --name <hpa-name > --cpu-percent=20 --min=1 --max=3
```

List all HPA:

```bash
kubectl get hpa
```

Show the details of a HPA:

```bash
kubectl describe hpa <hpa-name >
```

Delete HPA:

```bash
kubectl delete hpa <hpa-name >
```

Show the logs of the Metrics Server. Used to check the operational logs of the Metrics Server to diagnose issues, monitor its activities, or understand its interactions with other components in the cluster.

```bash
kubectl logs -n kube-system -l k8s-app=metrics-server
```


Stop the Kubernetes cluster managed by Kind, including all its control plane and worker nodes.

```bash
kind delete cluster --name your-cluster-name
```

------

# **Others**

# Repository structure

```bash
cookiecutter https://github.com/drivendata/cookiecutter-data-science

```


## **jupyter**

Convert notebook to markdown:

```bash
jupyter nbconvert --to markdown <notebook-name>.ipynb
```

## **Jekyll**

Create a new jekyll site and serve it locally:

```bash
jekyll new <site-name>
```

Run jekyll server locally:
```bash
bundle exec jekyll serve
```

## **Xelatex**

Convert jupyter notebook to latex and then to pdf:

```bash
jupyter nbconvert --to latex <notebook-name >.ipynb
```

Convert latex to pdf:

```bash
xelatex <notebook-name>.tex
```
