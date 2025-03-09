user@Syrex:~$ export GITHUB_USERNAME=Syrex333
user@Syrex:~$ GITHUB_EMAIL=ivanchernogorov579@gmail.com
user@Syrex:~$ export GITHUB_TOKEN=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
user@Syrex:~$ alias edit=nano


user@Syrex:~$ cd ${GITHUB_USERNAME}/workspace
user@Syrex:~/Syrex333/workspace$ source scripts/activate


user@Syrex:~/Syrex333/workspace$ mkdir ~/.config
user@Syrex:~/Syrex333/workspace$ cat > ~/.config/hub <<EOF
> github.com:
> - user: ${GITHUB_USERNAME}
> oauth_token: ${GITHUB_TOKEN}
> protocol: https
> EOF
user@Syrex:~/Syrex333/workspace$ cat > ~/.config/hub <<EOF
github.com:
- user: ${GITHUB_USERNAME}
oauth_token: ${GITHUB_TOKEN}
protocol: https
EOF
user@Syrex:~/Syrex333/workspace$ git config --global hub.protocol https


user@Syrex:~/Syrex333/workspace$  mkdir projects/lab02 && cd projects/lab02
user@Syrex:~/Syrex333/workspace/projects/lab02$ git init
Initialized empty Git repository in /home/user/Syrex333/workspace/projects/lab02/.git/
user@Syrex:~/Syrex333/workspace/projects/lab02$ git config --global user.name ${GITHUB_USERNAME}
user@Syrex:~/Syrex333/workspace/projects/lab02$ git config --global user.email ${GITHUB_EMAIL}
user@Syrex:~/Syrex333/workspace/projects/lab02$ git config -e --global
hint: Waiting for your editor to close the file...

Use "fg" to return to nano.

[1]+  Stopped                 git config -e --global

user@Syrex:~/Syrex333/workspace/projects/lab02$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab02.git
user@Syrex:~/Syrex333/workspace/projects/lab02$ git pull origin master
fatal: couldn't find remote ref master
user@Syrex:~/Syrex333/workspace/projects/lab02$ touch README.md
user@Syrex:~/Syrex333/workspace/projects/lab02$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md

nothing added to commit but untracked files present (use "git add" to track)
user@Syrex:~/Syrex333/workspace/projects/lab02$ git add README.md
user@Syrex:~/Syrex333/workspace/projects/lab02$ git commit -m"added README.md"
[master (root-commit) ca563f1] added README.md
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md
user@Syrex:~/Syrex333/workspace/projects/lab02$  git push origin master
Username for 'https://github.com': Syrex333
Password for 'https://Syrex333@github.com':
remote: Support for password authentication was removed on August 13, 2021.
remote: Please see https://docs.github.com/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls for information on currently recommended modes of authentication.
fatal: Authentication failed for 'https://github.com/Syrex333/lab02.git/'




user@Syrex:~/Syrex333/workspace/projects/lab02$ git pull origin main
warning: no common commits
remote: Enumerating objects: 6, done.
remote: Counting objects: 100% (6/6), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 6 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Unpacking objects: 100% (6/6), 2.36 KiB | 1.18 MiB/s, done.
From https://github.com/Syrex333/lab02
 * branch            main       -> FETCH_HEAD
 * [new branch]      main       -> origin/main
fatal: refusing to merge unrelated histories
user@Syrex:~/Syrex333/workspace/projects/lab02$ git log
commit ca563f127df15819babc498730eca1abbd653a28 (HEAD -> master)
Author: Syrex333 <ivanchernogorov579@gmail.com>
Date:   Sat Mar 8 14:47:12 2025 +0300

    added README.md



user@Syrex:~/Syrex333/workspace/projects/lab02$ mkdir sources
user@Syrex:~/Syrex333/workspace/projects/lab02$ mkdir include
user@Syrex:~/Syrex333/workspace/projects/lab02$ mkdir examples
user@Syrex:~/Syrex333/workspace/projects/lab02$ cat > sources/print.cpp <<EOF
> #include <print.hpp>
>
> void print(const std::string& text, std::ostream& out)
> {
>   out << text;
> }
void pri>
> void print(const std::string& text, std::ofstream& out)
> {
>   out << text;
> }
> EOF




user@Syrex:~/Syrex333/workspace/projects/lab02$ cat > include/print.hpp <<EOF
> #include <fstream>
> #include <iostream>
> #include <string>
>
> void print(const std::string& text, std::ofstream& out);
> void print(const std::string& text, std::ostream& out = std::cout);
> EOF


user@Syrex:~/Syrex333/workspace/projects/lab02$ cat > examples/example1.cpp <<EOF
> #include <print.hpp>

int mai>
> int main(int argc, char** argv)
> {
>   print("hello");
> }
> EOF




user@Syrex:~/Syrex333/workspace/projects/lab02$ cat > examples/example2.cpp <<EOF
> #include <print.hpp>
>
> #include <fstream>
>
> int main(int argc, char** argv)
> {
>   std::ofstream file("log.txt");
>   print(std::string("hello"), file);
> }
> EOF


user@Syrex:~/Syrex333/workspace/projects/lab02$ edit README.md



user@Syrex:~/Syrex333/workspace/projects/lab02$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        examples/
        include/
        sources/

nothing added to commit but untracked files present (use "git add" to track)
user@Syrex:~/Syrex333/workspace/projects/lab02$ git add .
user@Syrex:~/Syrex333/workspace/projects/lab02$ git commit -m"added sources"
[master 036c29c] added sources
 4 files changed, 32 insertions(+)
 create mode 100644 examples/example1.cpp
 create mode 100644 examples/example2.cpp
 create mode 100644 include/print.hpp
 create mode 100644 sources/print.cpp
user@Syrex:~/Syrex333/workspace/projects/lab02$ git push origin master
Username for 'https://github.com': Syrex333
Password for 'https://Syrex333@github.com':
remote: Support for password authentication was removed on August 13, 2021.
remote: Please see https://docs.github.com/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls for information on currently recommended modes of authentication.
fatal: Authentication failed for 'https://github.com/Syrex333/lab02.git/'


