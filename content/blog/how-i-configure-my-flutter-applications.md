---
author: Yannick Seeger
title: "How I configure my Flutter Applications"
date: 2021-10-04T16:30:24+02:00
description: How to configure your Flutter Application
tags: ["programming", "flutter"]
summary: How to configure your Flutter Application.
---

In this article I will show you what I think is the best way to configure your Flutter Application.

---

Actually, it's not even long ago when I found out there is a thing called [`--dart-define`](https://dartcode.org/docs/using-dart-define-in-flutter/).
But how to use it?

It's simple as that.
If you run your application, you pass the configuration value as command line argument.

`flutter run --dart-define=BASE_URL=http://localhost:8008`
{{< highlight dart "linenos=table" >}}
const baseUrl = String.fromEnvironment('BASE_URL',
      defaultValue: 'https://api.project.com');
{{< / highlight >}}

If you are using Android Studio you can add the `--dart-define` parameter in the ***Additional run args*** form.
![Android Studio Run Args](https://i.imgur.com/y2AOxL2.png)
