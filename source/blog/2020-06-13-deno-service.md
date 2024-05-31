---
date: 2020-06-03
title: "Deno Service"
template: post
thumbnail: "../thumbnails/deno.jpg"
slug: deno-service
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

and again before we start, now deno has become 1.1.0, you can upgrade it by do **deno upgrade** in your terminal

In this video i will countinue to create service of handler.

first one, i want to make id as unix so to make it easy, i use library uuid create file createId.ts in service

```bash
import { v4 as uuid } from "https://deno.land/std/uuid/mod.ts";

export default () => uuid.generate();
```

next we will create service for db, for now db only write to json

```bash
import { DB_PATH } from "../config.ts";
import { Bahasa } from "../models/bahasa.ts";

export const fetchData = async (): Promise<Bahasa[]> => {
  const data = await Deno.readFile(DB_PATH);

  const decoder = new TextDecoder();
  const decodedData = decoder.decode(data);

  return JSON.parse(decodedData);
};

export const persistData = async (data): Promise<void> => {
  const encoder = new TextEncoder();
  await Deno.writeFile(DB_PATH, encoder.encode(JSON.stringify(data)));
};
```

create bahasa.ts in service

```bash
import { fetchData, persistData } from "./db.ts";
import { Bahasa } from "../models/bahasa.ts";
import createId from "../services/createId.ts";

type BahasaData = Pick<Bahasa, "title" | "author">;

export const getBahasas = async (): Promise<Bahasa[]> => {
  const bahasas = await fetchData();

  // sort by name
  return bahasas.sort((a, b) => a.title.localeCompare(b.title));
};

export const getBahasa = async (bahasaId: string): Promise<Bahasa | undefined> => {
  const bahasas = await fetchData();

  return bahasas.find(({ id }) => id === bahasaId);
};

export const createBahasa = async (bahasaData: BahasaData): Promise<string> => {
  const bahasas = await fetchData();

  const newBahasa: Bahasa = {
    id: createId(),
    title: String(bahasaData.name),
    author: String(bahasaData.role),
    added: new Date()
  };

  await persistData([...bahasas, newBahasa]);

  return newBahasa.id;
};

export const updateBahasa = async (
  bahasaId: string,
  bahasaData: BahasaData
): Promise<void> => {
  const bahasa = await getBahasa(bahasaId);

  if (!bahasa) {
    throw new Error("Bahasa not found");
  }

  const updatedBahasa = {
    ...bahasa,
    name: bahasaData.title !== undefined ? String(bahasaData.title) : bahasa.title,
    author: bahasaData.author !== undefined ? String(bahasaData.author) : bahasa.author,
  };

  const bahasas = await fetchData();
  const filteredBahasas = bahasas.filter(bahasa => bahasa.id !== bahasaId);

  persistData([...filteredBahasas, updatedBahasa]);
};

export const deleteBahasa = async (bahasaId: string): Promise<void> => {
  const bahasas = await getBahasas();
  const filteredBahasas = users.filter(bahasa => bahasa.id !== bahasaId);

  persistData(filteredBahasas);
};
```

and again i will define for error handling when failed to get route

i create new file named as error.ts
```bash
export default async ({ response }, next) => {
  try {
    await next();
  } catch (err) {
    response.status = 500;
    response.body = { msg: err.message };
  }
};
```
before we test this data i want to create example data in db/bahasas.json

```bash
[
  {
    "id": "1",
    "title": "PHP",
    "author": "Jone",
    "added": "2017-10-15"
  },
  {
    "id": "2",
    "title": "DART",
    "author": "Google",
    "added": "2017-10-15"
  }
]
```

and we can run it by do drun in terminal, and yes this is final part of basic deno, want to learn how to save to mysql or someting like mongodb, please give me comment

that it about model and route, next we will learn about handler to this route.

i hope you enjoy with this video, Don't forget to subscribe.

Thanks