# Introduction

It feels like nowadays our data gets used against us as much—if not more—than for us. With the current state of online tracking and surveillance, controlling *who* knows *what* about you is a daunting task.

Locking the digital doors and shuttering your Windows™ only goes so far.

Our goal is to render useless the kinds of data that are: scraped and sold by data brokers, collected by ISPs and companies for targeted advertising, used by Fortnite players and other malicious individuals for doxxing attacks, identity theft, and account takeovers, or by abusers, stalkers, governments, and law enforcement, for surveillance and harassment.

But first,
> Have you've heard about this week's sponsor, ShiTsec VPN with new *Shift*Blame™ technology? It's the free-to-play VPN service that's worth every penny! ShiTsec's patented technology works by selling you a subscription. It's that simple.

![ShiTsec](https://github.com/alicezwatson/personal-data-pollution/blob/b1fcf0df7328240a0821fdd22b287aeda762e859/shitsec.jpg)

Now back to our show.

# If Data is the New Oil, Let's Make a Molotov
This project is a work in progress. Take is with a grain of salt and a spoonful of sugar.

## Part I: Threat Modeling

### 1. Identifying Assets

This is an important initial step where you determine the data or assets you want to protect. For this project, we're going to focus on two groups of data: Personally Identifying Information (PII), and Behavioral Data (BD).

![Threads Permissions](https://github.com/alicezwatson/personal-data-pollution/blob/b1fcf0df7328240a0821fdd22b287aeda762e859/threads_permissions.png)

#### Personally Identifying Information (PII)
These are not only things like your real name, birth-date, address, physical descriptors, medical information, and photos, but also your IP address, browser fingerprint, online handles, and avatars.

The reason I include the last few as "personally identifying" is because it's often easy to pivot from someone's handle or profile picture on one service to their alt and real-name accounts on other services. If, for instance, a company were to have trackers across many sites (*cough* Google, Facebook), then they can build profiles and connect them by a common IP, cookie, or browser fingerprint.

#### Behavioral Data (BD)
This is information about what you do on and offline. If your [typical morning routine](https://xkcd.com/1518/) has you logging in to your Threads account to check the like-count on your latest post about NFTs, then Meta knows a good deal about you already.

### 2. Defining Adversaries

Here, you need to list potential threats or adversaries. They can range from your internet provider, data brokers, hackers, to even local or foreign government agencies.

### 3. Documenting Existing Security Measures

What measures are already in place to secure your data? List out any existing protection mechanisms such as firewalls, anti-virus software, VPNs, and more.

### 4. Evaluating Potential Threats

Analyze the potential threats that can jeopardize your data. Look at known vulnerabilities, past security incidents, and what could happen if those weaknesses were exploited.

### 5. Determining the Impact

Assess the potential impact for each identified threat. Consider the severity of the fallout if your data were breached or compromised.

### 6. Plan for Risk Mitigation

After identifying the risks and evaluating the impact, the next step is planning for risk mitigation. This involves selecting and prioritizing the measures or controls to reduce the risk of threats.

### 7. Regular Review and Update 

Threat modeling is not a one-time process. You should routinely review and update your model to account for new assets, threats, and vulnerabilities.


To construct a comprehensive security plan, one has to identify potential adversaries, identify the types of data that need protection, and strategize on how to protect these assets. The following sections provide a detailed breakdown:
