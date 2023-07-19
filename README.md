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

Threat modeling is a systematic approach to identify potential threats and vulnerabilities, that involves identifying assets, adversaries, attack surfaces, and making plans on how to mitigate those attacks or reduce the harm they can cause.


## 1. Identifying Assets

This is an important initial step where you determine the data or assets you want to protect. For this project, we're going to focus on two groups of data: Personally Identifying Information (PII), and Behavioral Data (BD).

![Threads Permissions](threads_permissions.png)

### Personally Identifying Information (PII)
PII is any data that could potentially identify a specific individual. This could be a range from full names, address, email addresses, to even biometric data. In certain cases, even IP addresses can be considered PII. Another sneaky form of PII is device fingerprinting, where characteristics of your device, such as its operating system, screen size, font libraries, etc., are used to build a unique profile. 

### Behavioral Data (BD)
Behavioral data, or consumer insights data, tracks user actions, habits, and decisions online. This can include everything from the links you click, to your social media activity, to your digital purchases, and much more.<br>

Besides being used for targeted advertising, manipulation of consumer habits, and micro-targeting in political campaigns (the Cambridge Analytica scandal immediately comes to mind), a less talked about use for this data comes in the form of routine identification—where you go and when you're vulnerable—which can be used by stalkers and abusers to find or track victims.


## 2. Defining Adversaries

We've already covered a number of adversaries above. For our purposes here, we'll use a more general definition:<br>
> **Anyone trying to piece together a broader or more detailed profile of us, who we did not explicitly intend to share such insights with.**


## 3. Understanding Existing Security Measures

If you're reading this, then you may have already taken some precautions around your personal data privacy. If not, we'll cover some options and their effectiveness here.<br>


### Privacy-Respecting Browsers and Search Engines

#### Private Browsing and Incognito Modes
> These do basically nothing to protect you from online tracking. They will, however, offer some protection from users *on the same device* viewing your browsing history or accessing your account on a site you were logged into.<br>
> *Source: [Away From Prying Eyes: Analyzing Usage and Understanding of Private Browsing](https://www.usenix.org/system/files/conference/soups2018/soups2018-habib-prying.pdf)*<br>

> "We show that correctly implementing private browsing can be non-trivial, and in fact, all browsers fail in one way or another."<br>
> *Source: [An Analysis of Private Browsing Modes in Modern Browsers](https://www.usenix.org/legacy/events/sec10/tech/full_papers/Aggarwal.pdf)*<br>

#### Private Search Engines
> Private search engines function like regular search engines, but take measures to remove PII or disassociate it from the search queries.<br>
> My personal recommendation (and the one I use) is [StartPage.com](https://www.startpage.com/), who provides solid anonymity and good results (through Google's site index).
> *Source: [Which private search engine is the most private?](https://www.startpage.com/privacy-please/privacy-advocate-articles/private-search-engine-comparison)*


### VPNs
VPNs have their place, such as when access to online resources is geo-restricted, but when it comes to security, they're more about shifting trust.<br>
Now that most of the web supports HTTPS, and most browsers warn of sites that don't, the perks of using a VPN have diminished considerably.<br>

"Many of the most popular VPN services are now also less trustworthy than in the past because they have been bought by larger companies with shady track records."<br>
*Source: [It’s Time to Stop Paying for a VPN](https://www.nytimes.com/2021/10/06/technology/personaltech/are-vpns-worth-it.html)*

If you want to shift that trust to yourself, and you have some technical aptitude, then you can run your own VPN (such as [Algo VPN](https://github.com/trailofbits/algo)) for cheap-to-free.


### Browser Plugins
There are a billion browser plugins out there that claim to provide security. However, they come with the same issues as many VPNs—you're trusting a 3rd party (often a single developer) to protect you.<rb>
Now, I'm not shitting on browser plugins; in fact, I'm going to cover some in-depth later on. But for now, there are a couple that do what they say on the label, and are worth noting here:<br>
- [AdNauseam](https://adnauseam.io/) — AdNauseam incorporates [uBlock Origin](https://ublockorigin.com/) and, alongside blocking ads, it clicks all of them.
- [Random User-Agent](https://github.com/tarampampam/random-user-agent) — This addon randomizes your browser's user-agent and changes it every few minutes.


## 4. Evaluating Potential Threats

Analyze the potential threats that can jeopardize your data. Look at known vulnerabilities, past security incidents, and what could happen if those weaknesses were exploited.


## 5. Determining the Impact

Assess the potential impact for each identified threat. Consider the severity of the fallout if your data were breached or compromised.


## 6. Plan for Risk Mitigation

After identifying the risks and evaluating the impact, the next step is planning for risk mitigation. This involves selecting and prioritizing the measures or controls to reduce the risk of threats.


## 7. Regular Review and Update 

Threat modeling is not a one-time process. You should routinely review and update your model to account for new assets, threats, and vulnerabilities.


To construct a comprehensive security plan, one has to identify potential adversaries, identify the types of data that need protection, and strategize on how to protect these assets. The following sections provide a detailed breakdown:
