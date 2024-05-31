---
date: 2020-06-03
title: "Deno Model and Route"
template: post
thumbnail: "../thumbnails/deno.jpg"
slug: deno-model-and-route
categories:
  - Deno
  - Programming
tags:
  - blog
  - deno
  - basic
  - model
  - route
---

[![Deno Configuration](https://img.youtube.com/vi/FzjQHu_Cp9E/0.jpg)](https://www.youtube.com/watch?v=FzjQHu_Cp9E)

Hello everyone, iam fiaz luthfi and now you are on devindo youtube channel. in this video i will continue tutorial about deno, if you forget previous video, the link is above here. 

and again before we start, now deno has become 1.0.4, you can upgrade it by do **deno upgrade** in your terminal

In this video i will talk about how create model data and how to create routeing.

let's jumpt to the first one. Before i have example data bahasa, there is

```bash
id
title
author
```

i will create this data to model, this example can be generailze, so if you have big data, you can modeling as your data, we know tipe data not much string, boolean, date, integer, double just that. so if you don't know about this, please give me comment

i create new file named as bahasa.ts
```bash
export interface User {
  id: String;
  title: string;
  author: string;
  // because this will save to database so better to add field date.
  added: Date;
}
```
next go to routing.ts, we will create routing CRUD

```bash
import { Router } from "https://deno.land/x/oak/mod.ts";

const router = new Router();

router
  .get("/bahasa", getBahasa)
  .get("/bahasa/:id", getBahasaDetails)
  .post("/bahasa", createBahasa)
  .put("/bahasa/:id", updateBahasa)
  .delete("/bahasa/:id", deleteBahasa);

export default router;
```

its became error cause we not create function to this refrence, we learn this next video,

last because we have define route we can change initial this to index.ts. remove router in this place.

```bash
import router from "./routing.ts";

// remove
const router = new Router();
```

that it about model and route, next we will learn about handler to this route.

i hope you enjoy with this video, and please give me comment. Don't forget to subscribe.

Thanks