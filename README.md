# If Data is the New Oil, Let's Make a Molotov
This project is a work in progress.<br>
Take is with a grain of salt and a spoonful of sugar.<br>
Right now it is pretty much just the intro and some placeholder sections on threat modeling.


# Introduction

It feels like nowadays our data gets used against us as much—if not more—than for us.<br>
With the current state of online tracking and surveillance, controlling *who* knows *what* about you is a daunting task.

Locking the digital doors and shuttering your Windows™ only goes so far.

Our goal is to render as useless as possible the kinds of data that are: scraped and sold by data brokers, collected by ISPs and companies for targeted advertising, used by Fortnite players and other malicious individuals for doxxing attacks, identity theft, and account takeovers, or by abusers, stalkers, governments, and law enforcement, for surveillance and harassment.

If you're keen on some real-world examples of how your data is used, here are a few:

> ### **Data Brokers**<br>
> Watch [Data Brokers: Last Week Tonight with John Oliver (HBO)](https://www.youtube.com/watch?v=wqn3gR1WTcA). It's scary and funny.
>
> The Department of Homeland Security and FBI have been purchasing personal data from brokers, including cell phone location data and home address information, circumventing democratic accountability as these agencies buy the data without warrants.<br>
> *Source: [Data Brokers Are a Threat to Democracy](https://www.wired.com/story/opinion-data-brokers-are-a-threat-to-democracy/)*
>
> Travel website Orbitz showed more expensive options to Mac users, assuming they were wealthier.<br>
> Equifax's credit reporting division sold “prescreened” lists of consumers late on their mortgage payments to Direct Lending Source, who resold them to entities marketing loan modification and debt relief services.<br>
> Teletrack, Inc. also paid a penalty for selling lists of consumers who applied for non-traditional credit products, including payday loans, to third parties for marketing purposes.<br>
> *Source: [A Review of the Data Broker Industry: Collection, Use, and Sale of Consumer Data for Marketing Purposes](https://www.commerce.senate.gov/services/files/bd5dad8b-a9e8-4fe9-a2a7-b17f4798ee5a)*

> ### **Stalking and Abuse**<br>
> In the case of online victimization, certain information might facilitate the offender’s pursuit of the victim (e.g., e-mail addresses, instant messenger IDs) or make the individual a more desirable target (e.g., posting relationship status, photos, sexual orientation), thereby increasing an individual’s attractiveness as a target.<br>
> *Source: [Being Pursued Online: Applying Cyberlifestyle–Routine Activities Theory to Cyberstalking Victimization](https://citeseerx.ist.psu.edu/document?repid=rep1&type=pdf&doi=72d7a292f41dd1f97555893e995a8765a2d04db9)*

> ### **Photos and Facial Recognition**<br>
> During the 2015 protests following Freddie Gray's death, the Baltimore County Police Department used facial recognition in combination with social media monitoring to track protesters.<br>
> The police ran photos from social media posts through Maryland's facial recognition technology, enabling them to directly arrest individuals from the crowd.<br>
> *Source: [Clare Garvie's 2019 hearing at the House of Representatives](https://www.congress.gov/116/meeting/house/109521/witnesses/HHRG-116-GO00-Wstate-GarvieC-20190522.pdf)*
> 
> In 2017, a suspect was captured on camera allegedly stealing beer from a CVS in New York City.<br>
> When the low-quality surveillance image returned no matches on the NYPD's facial recognition system, the detectives used a high-quality images of actor Woody Harrelson, who bore some resemblance to the suspect.<br>
> Using this method, they identified and arrested someone for petty larceny.<br>
> *Source: [Clare Garvie, Garbage In, Garbage Out](https://www.flawedfacedata.com/)*

---

*Advertisement*<br>
> Special thanks to this week's sponsor, ShiTsec VPN with *Shift*Blame™ technology.<br>
> It's the free-to-play VPN service that's worth every penny!<br>
> ShiTsec's patented technology works by selling your data. It's that simple.<br>

![ShiTsec](shitsec.png)

---

# Part I: Threat Modeling

### 1. Identifying Assets

This is an important initial step where you determine the data or assets you want to protect. For this project, we're going to focus on two groups of data: Personally Identifying Information (PII), and Behavioral Data (BD).

![Threads Permissions](threads_permissions.png)

#### Personally Identifying Information (PII)
These are not only things like your real name, birth-date, address, physical descriptors, medical information, and photos, but also your IP address, browser fingerprint, online handles, and avatars.

The reason I include the last few as "personally identifying" is because it's often easy to pivot from someone's handle or profile picture on one service to their alt and real-name accounts on other services. If, for instance, a company were to have trackers across many sites (*cough* Google, Facebook), then they can build profiles and connect them by a common IP, cookie, or browser fingerprint.

#### Behavioral Data (BD)
This is information about what you do on and offline. If your [typical morning routine](https://xkcd.com/1518/) has you logging in to Threads to check the like-count on your latest post about NFTs, then Meta knows a good deal about you already.

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
