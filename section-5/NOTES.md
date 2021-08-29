# Notes

## Links
1. [https://docs.docker.com/storage/](https://docs.docker.com/storage/)
2. [https://medium.com/@kelseyhightower/12-fractured-apps-1080c73d481c#.cjvkgw4b3](https://medium.com/@kelseyhightower/12-fractured-apps-1080c73d481c#.cjvkgw4b3)
3. [https://12factor.net/](https://12factor.net/)
4. [https://www.oreilly.com/radar/an-introduction-to-immutable-infrastructure/](https://www.oreilly.com/radar/an-introduction-to-immutable-infrastructure/)
5. [https://jekyllrb.com/](https://jekyllrb.com/)

## Shell Differences for Path Expansion
In the next lecture, you'll learn how to share files and directories between a host and a Docker container. One of the parts of the command line you'll need to type is the host file path you want to share.

With Docker CLI, you can always use a full file path on any OS, but often you'll see me and others use a "parameter expansion" like $(pwd) which means "print working directory".

Here's the important part. Each shell may do this differently, so here's a cheat sheet for which OS and Shell your using. I'll be using $(pwd) on a Mac, but yours may be different!

This isn't a Docker thing, it's a Shell thing.

For PowerShell use: ${pwd} 

For cmd.exe "Command Prompt use: %cd%

Linux/macOS bash, sh, zsh, and Windows Docker Toolbox Quickstart Terminal use: $(pwd) 

Note, if you have spaces in your path, you'll usually need to quote the whole path in the docker command.

## Database Passwords in Containers
We all know databases usually need passwords, but since the dawn of Docker, the postgres image (and a few others like redis) has allowed you to do a simple docker run on it and it starts without a password. Sure you could set a password but it didn't require one.

In Feburary 2020 that changed, and will affect using postgres in this course (and my others). When running postgres now, you'll need to either set a password, or tell it to allow any connection (which was the default before this change).

For docker run, and the forthcoming Docker Compose sections, you need to either set a password with the environment variable:

POSTGRES_PASSWORD=mypasswd

Or tell it to ignore passwords with the environment variable:

POSTGRES_HOST_AUTH_METHOD=trust

Note this change was in the Docker Hub image, and not a change in postgres itself.

Also note if I or you were pinning versions, as we should, this wouldn't have surprised us. I tend to only pin to the minor version in this course (9.6) rather than the patch version (9.6.16) to keep you a bit more secure in the course. In the real world, I always pin my production apps to the patch version. It's the only safe way to operate. By pinning to the minor version in the courses, I prevent any major changes from breaking the course (in theory ha ha), yet also ensure you're running the latest patches (which would fix any bugs or security problems). In this, *very rare case*, the maintainer of the official postgres decided to introduce a breaking change in the *image* to a patch release of the app. The two aren't related, and it kinda shows off a weakness of the Docker Hub model... that there is no version of the Docker Hub image really, it's just tracking the upstream postgres versions... so then if any Docker Hub change would break something, it can't easily be tracked as a separate version from the app itself. Oh well, just remember to always pin the whole image version for things you care about.

I've updated the course repo files to indicate this change, but if you've cloned the repo before February 18th, 2020, you will need to update or replace your clone.