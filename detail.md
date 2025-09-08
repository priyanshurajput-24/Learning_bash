# Useful Commands with Comments

## SSH Key and Access

### Generate an SSH key
```bash
ssh-keygen -t rsa -b 4096 -C "Container_service_to_CAD_gpu"
```
Generates a new RSA SSH key with 4096-bit encryption. Replace the comment (`-C`) with your desired identifier.

### Set correct permissions for SSH files
```bash
chmod 600 /Users/103391/.ssh/Container_Services_ssh
chmod 700 /Users/103391/.ssh
```
Ensures the private key file is secure and the `.ssh` directory has the correct permissions.

### Add public key to server and SSH into it
```bash
ssh -i /Users/103391/.ssh/Container_Services_ssh root@216.48.191.47
```
Accesses the server using the private key file.

### SSH config entry
```
Host Container_service
  HostName 216.48.191.47
  User root
  IdentityFile /Users/103391/.ssh/Container_Services_ssh
```
Simplifies SSH access by adding an entry to the SSH config file. Now you can just run `ssh Container_service`.

## Docker Commands

### Access a running Docker container
```bash
docker exec -it <container_id> bash
```
Opens an interactive bash shell inside the specified running Docker container.

### View a file inside a Docker container
```bash
docker exec -it <container_id> cat /var/log/fastapi-app.err.log
```
Displays the contents of a specific log file inside the container.

### Copy files to/from Docker containers
```bash
# From local to container
docker cp <local-path> <container-id>:<container-path>

# From container to local
docker cp <container-id>:<container-path> <local-path>
```
Transfers files between your local system and the Docker container.

### Run a Docker container with port mapping
```bash
docker run -d -p 8050:8009 my-fastapi-app
```
Maps port `8009` inside the container to port `8050` on your local system.

### Remove all Docker containers and images
```bash
docker rm -f $(docker ps -a -q)
docker rmi -f $(docker images -q)
```
Deletes all stopped containers and images to free up space.

## Celery and Redis

### Start Celery Flower for task monitoring
```bash
celery --broker=redis://164.52.192.40:8087/0 flower --basic-auth=user:pswd
```
Runs Celery Flower, a web-based tool for monitoring Celery tasks. Replace the broker URL and authentication details as needed.

## Port Management

### Find and kill processes on a specific port
```bash
# Find the process using the port
sudo netstat -tuln | grep ':80'

# Kill the process
sudo kill -9 $(sudo lsof -t -i:80)
```
Identifies processes running on port `80` and terminates them.

## File Management

### Replace a word in all files under a directory
```bash
LANG=C LC_CTYPE=C.UTF-8 find /path/to/root -type f -exec sed -i '' 's|routh|rty|g' {} +
```
Finds and replaces the word `routh` with `rty` in all files within the specified directory.

### Delete specific files
```bash
find . -name ".DS_Store" -type f -delete
```
Removes all `.DS_Store` files from the current directory and its subdirectories.

### Substitute words in a single file
```bash
sed -i '' 's/autotrain/autotrain121212/g' autotrain.log
```
Replaces `autotrain` with `autotrain121212` in the file `autotrain.log`.

### Substitute words in all files in a directory (Mac/Linux)
#### Mac:
```bash
for file in *.log; do
  if [ -f "$file" ]; then
    sed -i '.bak' 's/autotrain/autotrain121212/g' "$file"
  fi
done
```
#### Linux:
```bash
for file in *; do
  if [ -f "$file" ]; then
    sed -i.bak 's/autotrain/autotrain121212/g' "$file"
  fi
done
```
Replaces `autotrain` with `autotrain121212` in all files of the current directory, creating a backup with `.bak` extension.

## Networking and AWS

### Open a port on a server
```bash
sudo iptables -I INPUT -p tcp -m tcp --dport 80 -j ACCEPT
```
Allows incoming traffic on port `80`.

### AWS Configuration
```bash
aws configure --profile `name`
aws configure list-profiles
export AWS_PROFILE=profile_for_snare
```
Configures AWS CLI profiles and sets an environment variable for a specific profile.

## Miscellaneous

### Create a new Scala project
```bash
sbt new scala/scala-seed.g8
```
Sets up a new Scala project using the `sbt` seed template.

### Stop Conda base environment from activating by default
```bash
conda config --set auto_activate_base false
```
Prevents the base Conda environment from activating automatically upon opening a terminal.

### Save a dataset locally from Hugging Face
```python
from datasets import load_dataset

ds = load_dataset("SLTP/HLT-AA-C21-Alpaca")  # Replace with desired dataset

ds['train'].to_csv("data_11_train.csv")
```
Downloads a dataset from Hugging Face and saves the training split as a CSV file.

### Check disk usage
```bash
sudo du -h --max-depth=1 /root/.cache | sort -h
```
Displays the disk usage of directories under `/root/.cache` in human-readable format.

### Locate a specific file
```bash
find /usr/lib /usr/share /usr/local/lib /usr/local/share -name poppler-cpp.pc
```
Searches for the file `poppler-cpp.pc` in the specified directories.

### Copy content to clipboard
#### Linux:
```bash
cat filename | xclip -selection clipboard
```
#### Mac:
```bash
cat filename | pbcopy
```
Copies the contents of a file to the clipboard.

### Inspirational Quote
> Markets aren't driven by logic, but by stories we tell ourselves. When these stories become divorced from reality, bubbles form. And this bubble was about to burst...

### FastAPI with CORS
```python
from fastapi import FastAPI
from fastapi.middleware.cors import CORSMiddleware

app = FastAPI(title="FastAPI", description="API for processing Telecom_Bills files", version="0.1.0")

app.add_middleware(
    CORSMiddleware,
    allow_origins=["*"],
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)
```
Adds Cross-Origin Resource Sharing (CORS) middleware to a FastAPI app, allowing all origins, methods, and headers.


### Clone repo with particular user-account
```bash
git clone https://priyanshurajput-24@github.com/priyanshurajput-24/Learning_bash.git
```

* If finding trouble in git push with different user account in same system then git clone with above `syntax` type of command, then try to push again. It will work.


