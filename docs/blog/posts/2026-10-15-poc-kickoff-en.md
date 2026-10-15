---
date: 2026-10-15
authors:
  - Gamja1st
categories:
  - Project Plan
  - Kickoff
tags:
  - smartfarm
  - citrus
  - balcony
  - esp32
  - raspberrypi
  - quantum-annealing
  - stone-soup
---

# 🍊 [Plan] Growing Citrus on a Balcony: A 1-Year Smart Farm Project (feat. Quantum Annealing & Stone Soup)

> 🇰🇷 **[한국어 버전으로 읽기 (Read in Korean)](2026-10-15-poc-kickoff.md)**

Three years ago, I bought three 3-year-old citrus saplings and planted them in pots on my apartment balcony.  
Now, they've grown into sturdy little trees nearly a meter tall.  
Every spring, they bloom with fragrant white flowers, but none of them ever set fruit—every single blossom just withers and drops.  
I'm pretty sure the culprit is a lack of light.

My apartment faces southeast, which means direct sunlight disappears around 2 PM.  
Interestingly, flowering bulbs like freesias, lilies, and tulips bloom vigorously on the very same balcony.  
That tells me there's enough ambient light to initiate blooms, but not enough cumulative daily light (DLI: Daily Light Integral) to actually form and swell fruits.

So, the primary mission of this 1-year Smart Farm PoC is simple: **install grow lights, measure and optimize the light, and finally get these citrus trees to bear real fruit.**

<!-- more -->

---

## 🛠️ What I'm Planning to Build

### 1. Grow Lights & Light Optimization (Core)
* At the very least, use a **timer** to supplement light after the 2 PM sunlight cutoff.
* Integrate a **photoresistor (light sensor)** to measure in real-time how much the grow lights actually improve illumination.
* Convert lux readings into **DLI ($mol/m^2/day$)** to mathematically verify if we hit the ~20+ DLI threshold citrus fruits crave.

### 2. Soil Moisture Tracking & Telegram Notifications (Optional)
* Monitor soil moisture across all 3 pots so I know exactly when to water.
* Wire up a **Telegram bot** to ping my phone when moisture drops below a threshold.
* I already have an `INTELLIGENT SOIL DETECTOR` (measuring moisture, pH, temp, humidity), so I can cross-calibrate DIY sensors against ground truth.

### 3. Safe Auto-Watering (Anti-Flooding Design)
* Eventually, I'd like to add automated irrigation.
* Tapping directly into the balcony faucet with a motorized valve crossed my mind, but since this is an apartment, any leak could cause a disaster downstairs.
* Instead, I'll go with a fail-safe approach: **a 10L sealed water tank paired with a 5V/12V mini submersible pump**. Even in the worst-case glitch, it only ever spills what’s in the tank.

### 4. Servo-Driven Solar Reflector (Heliostat Experiment)
* To squeeze every drop out of natural sunlight, I want to mount a reflector on the balcony.
* A micro servo motor will rotate the reflector to track the sun's trajectory and bounce photons directly into the citrus canopy.
* I have a spare GPS module lying around, so I might even calculate the sun’s exact azimuth and elevation programmatically.

### 5. ESP32-CAM Time-Lapse
* Wake up once a day at noon, snap a high-res photo, push it to the Raspberry Pi, and go back to deep sleep.
* Putting together a time-lapse of blooming, hand-pollinating, and (hopefully) fruiting will be awesome.

---

## ⚛️ A Geeky Side Thought: Quantum Annealing for Citrus?

I’ve had a keen interest in quantum computing for a while and have read several books on it.  
When telling a friend about this project, I joked half-seriously:

> *"If this works out, maybe I'll optimize the whole balcony using a quantum computer. Quantum annealing is supposedly unmatched at solving combinatorial optimization problems, right?"*

Picture this: taking real-time solar angles, grow light spectra, power consumption, three pots' soil evaporation rates, and electricity tariff tiers, and mapping them all into a QUBO objective function on a D-Wave quantum annealer.  
Sure, running a quantum processor to nurture three potted citrus trees is like launching an interstellar starship to swat a fly... but wouldn't that be wonderfully ridiculous? (If this project succeeds, I might genuinely apply for D-Wave cloud free credits just for kicks!)

---

## 🛟 The Backup Plan: Strawberries or Lettuce!

Citrus trees only give you one shot a year. If fruit-set fails completely in the spring, I need a contingency.  
Under the same grow lights, I'll carve out space for **strawberries or quick-turn leafy greens like butterhead lettuce**.  
They offer fast feedback loops (1–2 months), ensuring we still get harvests, learning, and blog updates even if the oranges play hard to get.

---

## 🧰 Dusting Off My Electronics Stash

Over the years, I've hoarded quite a pile of hardware for "someday" projects. Time to put them to work:

* **Raspberry Pi 3 B+**: The central home server running Mosquitto (MQTT), SQLite, and the Telegram bot daemon.
* **ESP32 WROOM32**: The balcony edge controller reading analog sensors and driving servos and relays.
* **ESP32-CAM**: The dedicated time-lapse camera.
* **Smart Gateway (Zigbee/WiFi)**: Automating grow light smart plugs.
* **Freenove Raspberry Pi Ultimate Kit**: A treasure chest of servos, relays, LDRs, resistors, and breadboards.
* **Manual Lux Meter & Soil Detector**: Ground truth calibration instruments.

I've documented everything in the [Hardware Inventory](../../inventory.md).

---

## 🍲 The 'Stone Soup' Philosophy

I’ve always loved the old folk tale of **Stone Soup**.

A hungry traveler drops a simple stone into a pot of boiling water. Curious villagers ask what he's cooking.  
"A delicious stone soup," he says, "though it would be truly exquisite with just a carrot or an onion."  
One by one, villagers bring a potato, a piece of meat, or some herbs. In the end, everyone sits down to enjoy a rich, nourishing feast made together.

I see so many talented people around me with brilliant ideas who hesitate to start because they feel they aren’t fully prepared or don't have all the answers.

I hope this quirky, modest project—dusting off spare ESP32s and trying to coax fruit out of a 1-meter citrus tree on a balcony—can be **that first stone dropped into the pot**.

Whether you're a balcony gardener, an embedded hacker, or a plant enthusiast, feel free to chime in with advice, critique, or pull requests: *"Hey, I have that part too!"*, *"Try a makeup brush for pollination,"* or *"Here's how to model your QUBO."*

Let’s see if we can gather our ingredients and taste that sweet citrus together a year from now.

The pot is on the fire. Let's get cooking!

