# scanaki

Here some useful swarm commands:

# Isolating vm
docker node update --label-add hostuse=myvm myvm1
docker node update --label-add hostuse=myvm myvm2

# Create your service and run one puppet-agent per node using node's hostname as local hostname within the running container : 
docker service create -d --name "agent" --network puppet --mode global --constraint "node.labels.hostuse == myvm" --hostname "{{.Node.Hostname}}" thierryjl/puppet-agent

