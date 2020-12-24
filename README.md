# OpenDGA

Open-source Domain Generation Algorithm (DGA) library for Red Teams.

## Purpose of OpenDGA

DGA is an incredible tool for evading defense teams, and hiding your C2 communications in the mess of the internet. I love writing Red Team tooling, so I wanted to create a few DGA algorithms in various clients for Red Teams to use. Do Red Teams **need** DGA? Probably not.

## Usage

For usage, see the respective implementation folder.

## What is DGA?

[Domain Generation Algorithms (DGA)](https://en.wikipedia.org/wiki/Domain_generation_algorithm) are algorithms that automatically generate domains based off seeding data (which can take the form of a word, date, etc.). DGAs are used to prevent the defenders from simply blocking an IP or domain and thwarting C2 comms for attackers. An incredibly simple DGA is provided below, notice it is the same for an entire day, and then changes at midnight. So the attacker will have to pre-generate all the domains for the length of the campaign and register them.

```python
import datetime
import base64

def generate_dt():
    year = datetime.datetime.now().year 
    month = datetime.datetime.now().month
    day = datetime.datetime.now().day
    return "{}-{}-{}".format(year, month, day).encode('utf-8')


url = base64.b64encode(generate_dt()).decode('ascii').replace('=', '') + '.com' # MjAyMC0xMi0yNA.com on 12/23/2020
```