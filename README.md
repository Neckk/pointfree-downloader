## Debian/Ubuntu Startup Script

See `debian-startup-script.sh`

## Cookie Format
`cookies-pointfree.txt` and `cookies-swifttalk.txt` should be present in the working dir and have the first line:

```
# Netscape HTTP Cookie File
```

## Google Drive Setup
- download `client_secrets.json` from Google Developer Console
- on the first attempt to upload you would be requested to authenticate
and the `credentials.json` file will be stored for subsequent use

## Docker setup on Unraid
1. SSH to your unraid server
2. Obtain the code: `git clone https://github.com/neckk/pointfree-downloader && cd pointfree-downloader && git checkout neckk/pointfree_docker_support`
3. Create a directory for configuration files: `mkdir /mnt/user/appdata/pointfree-downloader`
4. Insert a proper cookies file to the newly created directory, ex. `touch /appdata/cookies-pointfree.txt` (NOTE: All files from the /appdata directory are linked to the script's working dir)
5. Create a directory for downloaded media files: `mkdir /mnt/user/Downloads/pointfree`
6. Build container image from dockerfile: `docker build -t pointfree-downloader -f PointFreeDockerfile .`
7. Run the container: `docker run -d -v /mnt/user/appdata/pointfree-downloader:/appdata -v /mnt/user/Downloads/pointfree:/downloads --name pointfree-downloader pointfree-downloader`
