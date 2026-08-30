1. The "All-in-One" Cleanup

Use these commands to clear multiple types of unused resources at once: 
- **Safe Cleanup:** `docker system prune`  
    Removes all stopped containers, unused networks, and dangling images (images not associated with any container).
- **Deep Cleanup:** `docker system prune -a`  
    Adds the removal of **all** unused images, not just dangling ones.
- **Total Purge:** `docker system prune -a --volumes`  
    Removes everything above plus all unused volumes. **Use with caution**, as volumes often contain persistent data.
2. Targeted Cleanup (By Resource)

If you only want to clean specific parts of Docker, use these individual commands:

- **Containers:** `docker container prune` — Removes all stopped containers.
- **Images:** `docker image prune -a` — Removes all images not used by at least one container.
- **Volumes:** `docker volume prune` — Removes all unused local volumes.
- **Networks:** `docker network prune` — Removes all networks not used by at least one container.
- **Build Cache:** `docker builder prune` — Clears the [Docker build cache](https://docs.docker.com/reference/cli/docker/builder/prune/) to free up space used during the image creation process.
3. Essential Inspection & Safety

Before and after cleaning, use these tools to monitor your usage:

- **Check Usage:** Run `docker system df` to see a breakdown of how much space images, containers, and volumes are currently consuming.
- **Filter by Time:** You can limit a cleanup to older items (e.g., older than 24 hours) using filters:  
    `docker image prune -a --filter "until=24h"`.
- **Auto-Cleanup:** When starting a temporary container, add the `--rm` flag to the `docker run` command so it deletes itself immediately upon exiting:  
    `docker run --rm <image_name>`. 