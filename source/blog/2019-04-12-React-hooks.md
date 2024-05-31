---
date: 2019-04-12
title: "React Hooks, penerapan di REST API"
template: post
thumbnail: "../thumbnails/react.png"
slug: react-hooks-penerapan-di-rest-api
categories:
  - Frontend
  - Popular
  - Programming
tags:
  - blog
  - react
  - hooks
  - restapi
---

Ga nyangka seminggu ini rasanya happy banget setelah terjun di project react. Iya gua sebelumnya jujur belum pernah nyentuh reactjs, kalo react native sih udah tapi ampun deh mumet mikirin untuk mobile pake react native tuh

Nah sampailah gua pertemuan dengan si react ini, kenapa? karena pertama pas gua mau jump ke proyek vue yang ya bisa di bilang gua tau kok kayaknya ribet ada library yang ga ada nih di vue tapi ada di react. Iya tau sendiri kan programmer mah pengennya yang simple ga usah ribet bikin fungsi sendiri kalo udah ada yang bikin. Nah sampailah gua pada kebutuhan hooks ini, tapi sebenernya belum butuh banget sih, tapi sekalian lah buat catatan siapa tau nanti gua butuh untuk implement ini.

Oke langsung aja pertama kita bikin project react kosongan, pasti tau kan harus buka terminal? oke ikutin ini kalo udah

```bash
npx create-react-app du-hooks
cd du-hooks
npm start
```

apa bedanya npx dengan npm? sederhannya kalo npm mah harus instal atu-atu di lokal kita, kalo npx ga harus install langsung si fungsinya itu ngedownload dari cloud.

nah kalo pas npm start ada eror pajang banget coba baca, kalo ada warning SKIP_PREFLIGHT_CHECK=true nah pasang aja itu di env nya kalo selain itu coba di browsing erornya

karena kita fokusnya di penerapan hooks langsung saja maninan di `src/App.js

hapus dan ganti dengan kode berikut biar langsung ngikutin

```bash
import React, { Component } from "react";
import "./App.css";

class App extends Component {
  constructor() {
    super();
    this.state = {
      data: []
    };
  }
  componentDidMount() {
    axios.get("https://jsonplaceholder.typicode.com/posts").then(res => {
      const data = res.data;
      this.setState({
        data
      });
    });
  }
  render() {
    return (
      <div className="App">
        {this.state.data.map(item => (
          <p key={item.id}>{item.title}</p>
        ))}
      </div>
    );
  }
}

export default App;
```

Perlu penjelasan ga? ah tonton video gua aja ya

```bash
function App() {
  const [data, setData] = useState([]);

  useEffect(() => {
    axios
      .get("https://jsonplaceholder.typicode.com/posts")
      .then(result => setData(result.data));
  }, []);

  return (
    <div className="App">
      {data.map(item => (
        <p key={item.id}>{item.title}</p>
      ))}
    </div>
  );
}
```
nah di atas ini udah di convert ke hooks lebih simple kan? oke penjelasannya di video berikut ya

[devindo](https://youtube.com/devindo)

Semoga bermanfaat
