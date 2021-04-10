---
layout: post
tags: compsci
title: Subscriptions on iOS
---
Apple's in-app purchase API is not exactly... ergonomic. Especially when it comes to subscriptions. I've been struggling with it again so I was combing through the Apple docs, which have admittedly gotten better. Clicking on a link that came with a WWDC presentation in the new Developer app, I found [this implementation](https://developer.apple.com/documentation/storekit/in-app_purchase/subscriptions_and_offers/determining_service_entitlement_on_the_server) by Apple themselves of a server that handles subscriptions. Specifically receipt verification, the core of Apple subscription API. It's not exactly idiomatic JavaScript but it's definitely worth a look if you're trying to add subscriptions to your app.