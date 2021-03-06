# Notes

## Links
1. [https://github.com/moby/moby/blob/master/image/spec/v1.md](https://github.com/moby/moby/blob/master/image/spec/v1.md)
2. [https://github.com/docker-library/official-images/tree/master/library](https://github.com/docker-library/official-images/tree/master/library)
3. [https://docs.docker.com/storage/storagedriver/](https://docs.docker.com/storage/storagedriver/)
4. [https://docs.docker.com/engine/reference/builder/](https://docs.docker.com/engine/reference/builder/)

You can use "prune" commands to clean up images, volumes, build cache, and containers. Examples include:

- docker image prune to clean up just "dangling" images

- docker system prune will clean up everything

- The big one is usually docker image prune -a which will remove all images you're not using. Use docker system df to see space usage.

Remember each one of those commands has options you can learn with --help.

Here's a YouTube video I made about it: https://youtu.be/_4QzP7uwtvI

Lastly, realize that if you're using Docker Toolbox, the Linux VM won't auto-shrink. You'll need to delete it and re-create (make sure anything in docker containers or volumes are backed up). You can recreate the toolbox default VM with docker-machine rm default and then docker-machine create