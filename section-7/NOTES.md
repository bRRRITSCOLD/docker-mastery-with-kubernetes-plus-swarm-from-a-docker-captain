# Notes

## Links
1. [https://www.youtube.com/watch?v=dooPhkXT9yI](https://www.youtube.com/watch?v=dooPhkXT9yI)
2. [https://www.youtube.com/watch?v=_F6PSP-qhdA](https://www.youtube.com/watch?v=_F6PSP-qhdA)
3. [https://speakerdeck.com/aluzzardi/heart-of-the-swarmkit-topology-management](https://speakerdeck.com/aluzzardi/heart-of-the-swarmkit-topology-management)
4. [https://www.youtube.com/watch?v=EmePhjGnCXY](https://www.youtube.com/watch?v=EmePhjGnCXY)
5. [http://thesecretlivesofdata.com/raft/](http://thesecretlivesofdata.com/raft/)
6. [https://docs.docker.com/engine/swarm/services/](https://docs.docker.com/engine/swarm/services/)
7. [https://docs.digitalocean.com/products/droplets/how-to/add-ssh-keys/](https://docs.digitalocean.com/products/droplets/how-to/add-ssh-keys/)
8. [https://www.bretfisher.com/docker-swarm-firewall-ports/](https://www.bretfisher.com/docker-swarm-firewall-ports/)
8. [https://www.digitalocean.com/community/tutorials/how-to-configure-custom-connection-options-for-your-ssh-client](https://www.digitalocean.com/community/tutorials/how-to-configure-custom-connection-options-for-your-ssh-client)
8. [https://docs.docker.com/machine/drivers/hyper-v/](https://docs.docker.com/machine/drivers/hyper-v/)
8. [https://www.digitalocean.com/?refcode=ee97875d52fa&utm_campaign=Referral_Invite&utm_medium=Referral_Program&utm_source=CopyPaste](https://www.digitalocean.com/?refcode=ee97875d52fa&utm_campaign=Referral_Invite&utm_medium=Referral_Program&utm_source=CopyPaste)

## UI Change For Service Create/Update
You may notice that when using docker service create  and update , that the CLI acts differently for some Lectures then your own Docker. This is due to a change in the way Docker CLI shows the service commands in 2017.

--detach is a new option that changes the CLI response after you run a command.
This is a good thing, and doesn't affect the functionality of Swarm. It's just a UI difference. I use various 2017 versions of Docker in this course, so you may see different output for your own service create/update commands vs. mine, which is fine.

History of changes to CLI output for service create/update:

Before 17.05, the service commands would immediately return to your shell prompt and the containers would be scheduled in the background (asynchronously). To check if they deployed properly you would need to use docker service ls and docker service ps.
Starting in 17.05 the service commands were given a --detach  option, which defaulted to true , but warned you each time about a future change to false . The create/update commands were still asynchronous.
Starting in 17.10 the --detach  default changes to false , so you'll always see the UI wait synchronously while service tasks are deployed/updated, unless you set --detach true  in each command.
For all stable versions after 17.12, just remember:

Use the defaults if you're interactive at the CLI, typing commands yourself.
Use --detach true  if you're using automation or shell scripts to get things done.

## Docker Machine Bug With Swarm
If you're planning to use docker-machine to create local VM's for Swarm, note there is a bug in 18.09.0 that prevents Swarm network ports from listening. This is fixed in 18.09.1 so make sure you have the latest Docker Desktop or Docker Toolbox and your VM's are up to date.

Current versions (October 2019) include:

docker version 19.03.2

docker-machine version 0.16.2

To ensure you have the latest Docker Toolbox, download it from the GitHub release page.

You'll know you're up to date when you do a docker-machine ls and the VM's have 18.09.1 or later.

To update existing docker-machine VM's, you can use docker-machine upgrade `<name of vm>`.