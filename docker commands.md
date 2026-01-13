## 📋 docker start – commands When a Docker container is stopped :
| Scenario                     | Command                                     | What it does                         | Notes                     |
| ---------------------------- | ------------------------------------------- | ------------------------------------ | ------------------------- |
| Start a stopped container    | `docker start sonarqube`                    | Starts an existing stopped container | Keeps same ports & config |
| Start using container ID     | `docker start 72beedf0a5ea`                 | Starts container by ID               | ID can be shortened       |
| Start multiple containers    | `docker start sonarqube my_react_container` | Starts more than one container       | Space-separated           |
| Restart container            | `docker restart sonarqube`                  | Stops then starts container          | Use if app is stuck       |








