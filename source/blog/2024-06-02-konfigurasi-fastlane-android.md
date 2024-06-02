---
date: 2024-06-02
title: "Konfigurasi fastlane android"
template: post
categories:
  - automation
tags:
  - blog
  - fastlane
---

Kadang pekerjaan yang berulang itu membosankan sama seperti upload file apk ataupun untuk ios kita harus build trus upload manual, itu sangat membosankan. Nah salah satu cara untuk mengotomatisasikannya kita bisa pake ci/cd tp kadang ribet juga karena di aturnya pas di push ke git, gimana caranya biar lebih mudah lagi

kita bisa pake fastlane 

pastiin kalian udah install fastlane dan ngikutin cara yang ada di dokumentasi resmi. Karena beneran sangat-sangat jelas

saya disini cuma mau nambahin gimana caranya mengatur ketika kamu punya dart define di flutter untuk envnya jadi ngaturnya cukup sederhana kayak gini

```
default_platform(:android)

platform :android do

  # Have an easy way to get the root of the project
  def root_path
    Dir.pwd.sub(/.*\Kfastlane/, '').sub(/.*\Kandroid/, '').sub(/.*\Kios/, '').sub(/.*\K\/\//, '')
  end

  # Have an easy way to run flutter tasks on the root of the project
  lane :sh_on_root do |options|
    command = options[:command]
    sh("cd #{root_path} && #{command}")
  end

  # Tasks to be reused on each platform flow
  lane :build do
    sh_on_root(command: "flutter build appbundle --dart-define-from-file=.env/prod.json --release")
  end

  lane :release do
    build
    # Upload to production test
    upload_to_play_store(
      track: 'production',
      aab: '../build/app/outputs/bundle/release/app-release.aab', # Update this path if your AAB is generated in a different location
      skip_upload_apk: true,
      skip_upload_images: true,
      skip_upload_screenshots: true,
      skip_upload_metadata: true,
      skip_upload_changelogs: true,
      skip_upload_aab: false,
    )
  end

end
```