---
date: 2020-05-27
title: "Deno Configuration"
template: post
thumbnail: "../thumbnails/deno.jpg"
slug: deno-configuration
categories:
  - Deno
  - Programming
tags:
  - blog
  - deno
  - basic
---

[![Deno Configuration](https://img.youtube.com/vi/FzjQHu_Cp9E/0.jpg)](https://www.youtube.com/watch?v=FzjQHu_Cp9E)

Hello everyone, iam fiaz luthfi and now you are on devindo youtube channel. in this video i will continue tutorial about deno, if you forget previous video, the link is above here. 

before it now deno has become 1.0.2, you can upgrade i by do **deno upgrade** in your terminal

and deno has official extension in visual studi code, you can,uninstall extension before if you instaled and install the official one.

first one in this video i will tell you how to create enviroment configuration, so this video will be short.

to easily manage project, i create stucture like this.

```bash
handlers
// handlers contains route handlers
middlewares
// middlewares provide functions that run on every request
models
// models contain model definitions
services
// services contains... services
config.ts
// config.ts contains global application configuration, yes in this video we talk about this.
index.ts
// before is server.ts, this is a entry point of the application
routing.ts
// routing.ts contains API routes
```

before, we have create resource.ts it will be rename in next video, and this grouping to models, now just move this recource model to look clean,

this become read error, just fix it by define new route in index.ts

we will go to config.ts, before we have define, port and default host is localhost.

in node you know like env, yes same in deno, i will make env in config.ts

```bash
const env = Deno.env.toObject();
export const APP_HOST = env.APP_HOST || "127.0.0.1";
export const APP_PORT = env.APP_PORT || 3000;
// next i define for db path, in basic i just want write db to local json
export const DB_PATH = env.DB_PATH || "./db/bahasa.json"
```
go back to index.ts

```bash
import {APP_HOST, APP_PORT} from "./config.ts"

// you can change app listen to
app.listen(`${APP_HOST}:${APP_PORT})
``` 

lets test this project. before i create example with drun, you can upgrade drun

```bash
deno install --allow-read --allow-run --unstable -f https://deno.land/x/drun@v1.1.0/drun.ts
```

if you have install drun before use -f to rewrite

to easily run this project, i create drun.json like example, just copy, and add --allow-env couse we use env

just run by type drun, and lets see how its work.

that it about enviroment configuration, next we will learn about routing and model

i hope you enjoy with this video, and please give me comment. Don't forget to subscribe.

Thanks