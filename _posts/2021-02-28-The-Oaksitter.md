---
layout: post
tags: compsci raspberrypi
---

![oaksitter_full]({{ '/images/oaksitter/full.jpeg' | relative_url}})
*Oaksitting*

Sometime in autumn of last year before the second lockdown, Emma and I went to Hampstead Heath for a Sunday walk. I took home three acorns that had just sprouted and planted them in little pots I still had from before. One took a very long time to continue growing, one eventually died but one started growing almost immediately. I decided to build a machine to take care of my oak for me: the oaksitter.

It's a relatively simple build with a pi zero that controls [two pumps](https://www.amazon.co.uk/gp/product/B07D7TN1BW/) through a [relay](https://www.amazon.co.uk/gp/product/B06XK6HCQC/). The pumps are connected to a water reservoir on one side and held in place by two pencils on the other. The reason I used two pumps is that the water throughput was very small and the water tended to seep immediately into the soil without spreading out horizontally. 

To minimise the danger of water coming in contact with elecricity or leaking onto the floor, I built a compartmentalized setup on three chairs. I also tried using a [moisture sensor](https://shop.pimoroni.com/products/grow-moisture-sensor-pack-of-3) but I couldn't get very accurate measurements and I eventually just ended up using a cronjob, watering twice a week.

![detail]({{ '/images/oaksitter/oak.jpeg' | relative_url}})
*A happy oak*