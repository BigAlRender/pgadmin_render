# pgAdmin on Render

> [!WARNING]
> This example utilizes a Private Service using a "Starter" instance type and a 1GB disk. 
>
> **THIS EXAMPLE WILL HAVE A COST**.
>
> See our [pricing page](https://render.com/pricing#compute).

Proof of concept to get [containerized pgAdmin](https://hub.docker.com/r/dpage/pgadmin4/) running on a Render Web Service.

1. Fork repo to your GitHub account

2. In your Render Dashboard: New > Blueprint

3. Select the forked repo and the `private_paid` branch

4. Choose a name and fill out `PGADMIN_DEFAULT_EMAIL` & `PGADMIN_DEFAULT_PASSWORD`

5. Click Apply

[Private Services](https://docs.render.com/private-services) are not publicly accessible. However, you can access it with an SSH tunnel.

1. Add your [SSH keys to your Render account](https://docs.render.com/ssh).

2. Connect with an SSH tunnel via another service in the account and region: 
```
ssh -L <local_machine_port>:<pgadmin_internal_host:port> <ssh_connection_host_in_same_region> -N
```
e.g.
```
ssh -L 5431:pgadmin-abcd:80 srv-xxxxxxx@ssh.oregon.render.com
```

3. Connect locally (with the tunnel example above, that would be http://localhost:5431)