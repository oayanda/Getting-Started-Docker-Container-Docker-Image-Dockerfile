# Docker Mounts

## Volume Mounts 

Volume mounts allow us to create a special directory managed by Docker that allows us to share data across containers.
Containers can write to the volume, and have that data persist even after the container is stopped or removed.
Below are some of the main commands we used while exploring volume mounts:

```bash
# Create and inspect a volume:

- $ docker volume create shared-vol
- $ docker volume inspect shared-vol
```

Run a container with the mount.
Note that the source is the name of the volume, and the target is the container directory where the mount’s volumes should populate.
Writing to this container directory and editing its contents will update the original volume directory:


```bash
docker run -it --name=bar --mount source=shared-vol,target=/src/shared ubuntu bash
 ```

## Bind Mounts

we learn about bind mounts.
Bind mounts allow us to connect a directory on the Docker host machine to one in the container.
This allows us to give the container new files and update the bound directory on the fly.

This is useful for projects that have a working directory where configuration files continually update.
However, a bind mount has a more fragile setup, since the mounted host directory can always change or disappear.

```bash
#Run a container with a bind mount:
- $ docker run -it --name=foo --mount type=bind,source=shared-vol,target=/src/shared ubuntu bash
```

## Tmpfs Mounts 

Tmpfs mounts allow us to have a temporary storage solution for Docker containers.
This allows us to write files during the lifetime of a container without having that data persist.

Why is this useful?

If the container generates sensitive information like secret files or private keys, by using a tmpfs mount, we can ensure that the data disappears once the container completes its course.

Run a container, in detached mode, with a tmpfs mount;
The destination represents the directory where the container can write the secret data that should disappear:

```bash
- $ docker run -dit --name=baz --mount type=tmpfs,destination=/tmpdir ubuntu bash
```

