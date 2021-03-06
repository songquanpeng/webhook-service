# Webhook Service

[![Try it in Gitpod now](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#https://github.com/songquanpeng/webhook-service)

## Build
```
make
```

## Usage
### Cli
You can use `./cli command` to run specified command.

Or you can use `./cli` to get into the cli's shell and execute commands.

#### Commands
1. n / new: create new webhook.
2. d / delete id: delete specified webhook.
3. m / modify id: modify existed webhook.
4. e / execute id: execute specified webhook.
5. l / list: list all webhooks.
6. s / search keyword: search webhooks by a keyword in name or description.
7. p / print id: print detail information of specified webhooks.
8. h / help: print help information. 
9. q / quit: quit cli shell.

### Server
Start server by run `./server` or `./server port`, the default port is 8080.

Start server with pm2: `pm2 start ./server --name webhook-service -- 8080`.

## User case: update blog when there is a new github commit
1. Firstly you should create a shell script that runs `git pull` and blog website update command.
2. Then you run the `cli` to create a new webhook, which executor is the path of the above script.
3. Copy the url from the output and register the webhook in your Github repo's webhook page.
4. Then when you push a new commit to this repo, Github will send a post request to the server which will execute the specified script.
