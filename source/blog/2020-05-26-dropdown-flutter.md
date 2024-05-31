---
date: 2020-05-26
title: "Create Dropdown in flutter"
template: post
thumbnail: "../thumbnails/flutter.jpg"
slug: create-dropdown-in-flutter
categories:
  - flutter
  - Programming
tags:
  - blog
  - blog
  - flutter
  - basic
---

[![Dropdown Flutter](https://img.youtube.com/vi/qoK21pEQoEw/0.jpg)](https://www.youtube.com/watch?v=qoK21pEQoEw)

Hello everyone, iam fiaz luthfi and now you are on devindo youtube channel. in this video i will tell you how to create dropdown with flutter, for first one we will create dropdown basic, and after that we create dropdown from list. when this is done you can create easily dropdown from local json or from rest api.

okey let’s jump to first one.

this is basic flutter project, you can be done to create this by do ‘flutter create name_project in your command line,

to create dropdown, you can do inside body of stateless or statefull
```bash
// this is initial param
var valueGender;
// and write in dropdown in the body
DropdownButton(
    hint: Text("Select Gender"),
    value: valueGender,
    items: <String>['Male', 'Female', 'Undifine'].map((value) {
        return DropdownMenuItem(
            child: Text(value),t
            value: value,
        );
    }).toList(),
    onChanged: (value) {},
),
```

you will look like this.
if you want to pass data when select dropdown, you can define, setter and getter for example

```bash
// before we set text to direcly know what inside value gender
Text('$valueGender')

// and setter
onChanged: (value) {
    setState({
        valueGender = value;
    })
},

```
let see how its work,

before we continue to next section, we can handle error when refresh or getting null by set default value
example

```bash
_valueGender = 'Male';
```

and the second, if you have many list in this dropdown, this code will look ugly, you can sparate this list direcly in your stateless or statefull, example i have list name of my friend

```bash
List<String> names = [
    'Rangga',
    'Renaldy',
    'Erwin',
    'Rendy',
    'Ruli'
]
// you can direcly call this list to your dropdown
items: names.map((value) {
    return DropdownMenuItem(
        child: Text(value),
        value: value,
    );
```

so how to create dropdown when value from rest api?, first you must set depedency http in your pubspec.yaml,

in this wi will parse data country from this REST API https://restcountries.eu/rest/v2/all
```bash
http: ^0.12.1

// import http on your page of project, you have learn advance of flutter you can sparate between logic and view, but in this tutorial i will show booth in one widget

import 'package:http/http.dart' as http;

String _baseUrl = "https://restcountries.eu/rest/v2/all";
String _valCountry;
List<dynamic> _dataCountry = List();
void getProvince() async {
    final respose = await http.get(_baseUrl); 
    var listData = jsonDecode(respose.body);
    setState(() {
      _dataCountry = listData;
    });
    print("data : $listData");
}

@override
void initState() {
    super.initState();
    getProvince(); 
}

DropdownButton(
    hint: Text("Select Province"),
    value: _valCountry,
    items: _dataCountry.map((item) {
    return DropdownMenuItem(
        child: Text(item['name']),
            value: item['name'],
        );
    }).toList(),
    onChanged: (value) {
        setState(() {
            _valCountry = value;
        });
    },
),
```
when you have a lot of data this method will take time, and you can _dataCountry has value or not to avoid error

```bash
if(_dataCountry.length > 0)
```

last in this tutorial is how to create dropdown image?, first define your image location in this example i put image in folder assets, so just define in pubspec.yaml
```
assets:
    - assets/

// so i have 3 image and i will create dropdown about this

String _filter = 'All'

DropdownButton<String>(
    underline: SizedBox(),
    hint: Image.asset(
              'assets/All.png',
              scale: 3,
    ),
    value: _filter,
    items: <String>['All', 'One', 'Two'].map((String value) {
        return DropdownMenuItem<String>(
            value: value,
            child: Row(
                children: <Widget>[
                    Image.asset(
                      'assets/$value.png',
                      scale: 3,
                    ),
                  ],
                ),
              );
        }).toList(),
    onChanged: (val) {
        setState({
            _filter = val
        })
    },
),
```

and this is all about dropdwon in flutter, i hope you enjoy with this tutorial, and please give me comment about this video. Don't forget to subscribe. 
Thanks