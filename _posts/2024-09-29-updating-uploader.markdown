---
layout: post
author: "Katherine Reid"
title:  "Updating the Uploader"
date:   2024-09-29 19:23:00 -0500
categories: "dts"
---

As far as laptops go, I've been a ThinkPad user for years. In the ten-odd years since I got my first laptop as a child, I only used two (pre-owned!) laptops: a ThinkPad X220 and a ThinkPad T460s. I used the T460s through three years of college, until a daemon of death finally visited and rendered one of the two RAM slots unusable and left me with only 4 GB of usable memory! On top of this, I suspect there was additional motherboard damage beyond my perception, causing random freezes if I tried holding the laptop with one hand or applying excess pressure to the left palm rest.

This was no way for a computer science major to live, so I looked at my options and decided on a new laptop: a [Framework 13](https://frame.work/). It wasn't a ThinkPad, and that was a difficult decsion to make: the keyboard itself would feel different and be arranged differently; there wouldn't be a trackpoint sitting between the G, H, and B keys; the touchpad wouldn't have three physical mouse buttons above them, and there wouldn't be nearly as many IO ports. However, the benefit of having a laptop with, _*checks notes*_, enough RAM to go into hibernation with more than 5 Firefox tabs open was worth it to me. I also really believe in the mission of the Framework company and wanted to support them. Lenovo can ~~eat !@#$~~ go drive the ThinkPad name further into the ground.

Now that I hve a fully operational computer, I've been a lot more productive, especially on Disco Tray work. I'm once again working on the admin portal I wrote for the Hendrix Today app last summer, adding features such as editing and deleting individual events that allow the department running Hendrix Today to do more without requesting a Disco Tray developer to log in to the Firebase portal and perform operations there.

Have you ever been really proud of a piece of code you wrote, only to revisit it several months later and be shockingly disappointed in your past self? Long story short I was sending data around in two different formats and storing both as `List<String?>`s. The latter weeks of the summer of 2023 were not good to me. Since getting my new laptop up and running, I've been hard at work rewriting much of the portal to use actual data classes and be more scalable than it was last year. After I did that, it was finally possible for me to add editing features into the database screen. It currently only allows editing for the `String` fields of an event, but it's better than nothing.

I've noticed that my functional programming experience has bled into how I write all other kinds of code. In a programming team meet a few weeks ago, I found myself trying to pattern match on a list in Python, and when writing a Dart function to translate a Firestore snapshot (of type `Map<String, dynamic>`) into a data class, I just rewrote the monadic bind for nullable objects and wrote the entire function in a bind chain:

```dart
U? then<T, U>(T? first, U? Function(T) next) => switch (first) {
    null => null,
    T t  => next(t),
}
```

I'm honestly pleasantly surprised at how many functional features Dart provides: first-class functions, immutable variables, expression-body function syntax, an expression-level switch statement, and an if-case statement for conditionally matching on one particular case and binding a variable with a stricter type within that case. It's not Haskell, but I can get things done in it. (Frankly, I think writing a cross-platform application in a pure functional language like Haskell would be a nightmare.)

With my summer research having been presented last week, my work on the Disco language is almost completely wrapped up, and I can return more effort to Disco Tray... Our department loves disco.