---
date: 2020-06-03
title: "Deno Handlers"
template: post
thumbnail: "../thumbnails/deno.jpg"
slug: deno-handlers
categories:
  - Deno
  - Programming
tags:
  - blog
  - deno
  - basic
  - handlers
---

[![Deno Configuration](https://img.youtube.com/vi/FzjQHu_Cp9E/0.jpg)](https://www.youtube.com/watch?v=FzjQHu_Cp9E)

Hello everyone, iam fiaz luthfi and now you are on devindo youtube channel. in this video i will continue tutorial about deno, if you forget previous video, the link is above here. 

In this video i will talk about route handlers.

before we have define in route.ts now i will define route file of file handle

```bash
import getBahasa from "./handlers/getBahasa.ts";
import getBahasaDetails from "./handlers/getBahasaDetails.ts";
import createBahasa from "./handlers/createBahasa.ts";
import updateBahasa from "./handlers/updateBahasa.ts";
import deleteBahasa from "./handlers/deleteBahasa.ts";
```

firs we create fo getbahasa, i create new file in handlers getBahasa.ts, 
first import i define here is getBahasa but its became error because we never create this file, but no problem we will do latter

```bash
import { getbahasa } from "../services/bahasa.ts";

export default async ({ response }) => {
  response.body = await getbahasa();
};
```

this function to return all data bahasa, this like express we can define respone from body.
next we create for getBahasaDetails.ts

```bash
import { getbahasa } from "../services/bahasa.ts";

export default async ({ params, response }) => {
  const bahasaId = params.id;

  if (!bahasaId) {
    response.status = 400;
    response.body = { msg: "Invalid bahasa id" };
    return;
  }

  const foundBahasa = await getbahasa(bahasaId);
  if (!foundBahasa) {
    response.status = 404;
    response.body = { msg: `User with ID ${bahasaId} not found` };
    return;
  }

  response.body = foundBahasa;
};
```
next for createBahasa.ts

```bash
import { getbahasa } from "../services/bahasa.ts";

export default async ({ request, response }) => {
  if (!request.hasBody) {
    response.status = 400;
    response.body = { msg: "Invalid bahasa data" };
    return;
  }

  const {
    value: { title, author }
  } = await request.body();

  if (!title) {
    response.status = 422;
    response.body = { msg: "Incorrect bahasa data. title are required" };
    return;
  }

  const bahasaId = await createUser({ title, author });

  response.body = { msg: "UserBahasa created", bahasaId };
};
```
next deletebahasa.ts

```bash
import { getbahasa } from "../services/bahasa.ts";

export default async ({ params, response }) => {
  const bahasaId = params.id;

  if (!bahasaId) {
    response.status = 400;
    response.body = { msg: "Invalid bahasa id" };
    return;
  }

  const foundBahasa = await getUser(bahasaId);
  if (!foundBahasa) {
    response.status = 404;
    response.body = { msg: `Bahasa with ID ${bahasaId} not found` };
    return;
  }

  await deleteBahasa(bahasaId);
  response.body = { msg: "Bahasa deleted" };
};
```
last i will create handle, if every route hit by user not found so i create noFound.ts

```bash
export default ({ response }) => {
  response.status = 404;
  response.body = { msg: "Not Found" };
};
```

and define this to index.ts

```bash
import notFound from "./handlers/notFound.ts";
app.use(notFound);
```

still work must we do, that it about handler, next we will learn about service as mention before

i hope you enjoy with this video, and please give me comment. Don't forget to subscribe.

Thanks