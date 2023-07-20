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
> Watch [Data Brokers: Last Week Tonight with John Oliver (HBO)](https://www.youtube.com/watch?v=wqn3gR1WTcA). It's scary and funny.<br>
>
> The Department of Homeland Security and FBI have been purchasing personal data from brokers, including cell phone location data and home address information, circumventing democratic accountability as these agencies buy the data without warrants.<br>
> *Source: [Data Brokers Are a Threat to Democracy](https://www.wired.com/story/opinion-data-brokers-are-a-threat-to-democracy/)*<br>
>
> Travel website Orbitz showed more expensive options to Mac users, assuming they were wealthier.<br>
> Equifax's credit reporting division sold “prescreened” lists of consumers late on their mortgage payments to Direct Lending Source, who resold them to entities marketing loan modification and debt relief services.<br>
> Teletrack, Inc. also paid a penalty for selling lists of consumers who applied for non-traditional credit products, including payday loans, to third parties for marketing purposes.<br>
> *Source: [A Review of the Data Broker Industry: Collection, Use, and Sale of Consumer Data for Marketing Purposes](https://www.commerce.senate.gov/services/files/bd5dad8b-a9e8-4fe9-a2a7-b17f4798ee5a)*<br>

> ### **Stalking and Abuse**<br>
> In the case of online victimization, certain information might facilitate the offender’s pursuit of the victim (e.g., e-mail addresses, instant messenger IDs) or make the individual a more desirable target (e.g., posting relationship status, photos, sexual orientation), thereby increasing an individual’s attractiveness as a target.<br>
> *Source: [Being Pursued Online: Applying Cyberlifestyle–Routine Activities Theory to Cyberstalking Victimization](https://citeseerx.ist.psu.edu/document?repid=rep1&type=pdf&doi=72d7a292f41dd1f97555893e995a8765a2d04db9)*<br>

> ### **Photos and Facial Recognition**<br>
> During the 2015 protests following Freddie Gray's death, the Baltimore County Police Department used facial recognition in combination with social media monitoring to track protesters.<br>
> The police ran photos from social media posts through Maryland's facial recognition technology, enabling them to directly arrest individuals from the crowd.<br>
> *Source: [Clare Garvie's 2019 hearing at the House of Representatives](https://www.congress.gov/116/meeting/house/109521/witnesses/HHRG-116-GO00-Wstate-GarvieC-20190522.pdf)*<br>
> 
> In 2017, a suspect was captured on camera allegedly stealing beer from a CVS in New York City.<br>
> When the low-quality surveillance image returned no matches on the NYPD's facial recognition system, the detectives used a high-quality images of actor Woody Harrelson, who bore some resemblance to the suspect.<br>
> Using this method, they identified and arrested someone for petty larceny.<br>
> *Source: [Clare Garvie, Garbage In, Garbage Out](https://www.flawedfacedata.com/)*<br>

---

*Advertisement*<br>
> Special thanks to this week's sponsor, ShiTsec VPN with *Shift*Blame™ technology.<br>
> ShiTsec is the only the free-to-play VPN service that's worth every penny!<br>
> ShiTsec's patented technology works by selling your data. It's that simple.<br>

![ShiTsec](shitsec.png)

---

# Part I: Threat Modeling

Threat modeling is a systematic approach to identify potential threats and vulnerabilities, that involves identifying assets, adversaries, attack surfaces, and making plans on how to mitigate those attacks or reduce the harm they can cause.<br>


## 1. Identifying Assets

Before we can talk about ***how*** to protect ourselves, we need to determine the data or assets we want to protect.<br>
For this project, we're going to focus on two groups of data: Personally Identifying Information (PII), and Behavioral Data (BD).<br>

![Threads Permissions](threads_permissions.png)

### 1.1. Personally Identifying Information (PII)

PII is any data that could potentially identify a specific individual. This could be a range from full names, address, email addresses, to even biometric data. In certain cases, even IP addresses can be considered PII. Another sneaky form of PII is device fingerprinting, where characteristics of your device, such as its operating system, screen size, font libraries, etc., are used to build a unique profile.<br>


### 1.2. Behavioral Data (BD)

Behavioral data, or consumer insights data, tracks user actions, habits, and decisions online. This can include everything from the links you click, to your social media activity, to your digital purchases, and much more.<br>

Besides being used for targeted advertising, manipulation of consumer habits, and micro-targeting in political campaigns (the Cambridge Analytica scandal immediately comes to mind), a less talked about use for this data comes in the form of routine identification—where you go and when you're vulnerable—which can be used by stalkers and abusers to find or track victims.<br>


### 1.3 Now Do Some Soul Searching

- StartPage (Google results): https://www.startpage.com/sp/search?q="ALICE+WATSON"
- DuckDuckGo: https://duckduckgo.com/?q="ALICE+WATSON"
- SearX: https://searx.org/search?q="ALICE+WATSON"

- Google: https://www.google.com/?q="ALICE+WATSON"
- Bing: https://www.bing.com/search?q="ALICE+WATSON"
- Yandex: https://yandex.com/search/?text="ALICE+WATSON"

- Whats My Name: https://whatsmyname.app/?q="ALICE+WATSON"
- Am I Unique: https://amiunique.org/fingerprint

Make a note of what you find. How many results are actually you? How many results are someone with the same name/handle?<br>
I recommend opening your favorite text editor (I use [Kate](https://kate-editor.org/) and [Obsidian](https://obsidian.md/)), and copying the URLs that accurately identify you.<br>
You can add notes about what data each URL exposes, such as social, location, real name, etc.<br>
Keep this list handy, as you'll be revisiting it as you muck up your data.<br>


## 2. Identifying Adversaries

We've already mentioned a number of adversaries above. For our purposes here, we'll use a more general definition:<br>
> **Anyone trying to piece together a broader or more detailed profile of us, who we did not explicitly intend to share such insights with.**<br>


## 3. Understanding Existing Security Measures

What are we already doing and how well does it work?<br>


### 3.1. Privacy-Respecting Browsers and Search Engines


#### 3.1.1. Private Browsing and Incognito Modes
> These do basically nothing to protect you from online tracking. They will, however, offer some protection from users *on the same device* viewing your browsing history or accessing your account on a site you were logged into.<br>
> *Source: [Away From Prying Eyes: Analyzing Usage and Understanding of Private Browsing](https://www.usenix.org/system/files/conference/soups2018/soups2018-habib-prying.pdf)*<br>

> "We show that correctly implementing private browsing can be non-trivial, and in fact, all browsers fail in one way or another."<br>
> *Source: [An Analysis of Private Browsing Modes in Modern Browsers](https://www.usenix.org/legacy/events/sec10/tech/full_papers/Aggarwal.pdf)*<br>


#### 3.1.2. Private Search Engines
> Private search engines function like regular search engines, but take measures to remove PII or disassociate it from the search queries.<br>
> My personal recommendation (and the one I use) is [StartPage.com](https://www.startpage.com/), who provides solid anonymity and good results (through Google's site index).<br>
> *Source: [Which private search engine is the most private?](https://www.startpage.com/privacy-please/privacy-advocate-articles/private-search-engine-comparison)*<br>


### 3.2. VPNs
VPNs have their place, such as when access to online resources is geo-restricted, but when it comes to security, they're more about shifting trust.<br>
Now that most of the web supports HTTPS, and most browsers warn of sites that don't, the perks of using a VPN have diminished considerably.<br>

"Many of the most popular VPN services are now also less trustworthy than in the past because they have been bought by larger companies with shady track records."<br>
*Source: [It’s Time to Stop Paying for a VPN](https://www.nytimes.com/2021/10/06/technology/personaltech/are-vpns-worth-it.html)*<br>

If you want to shift that trust to yourself, and you have some technical aptitude, then you can run your own VPN (such as [Algo VPN](https://github.com/trailofbits/algo)) for cheap-to-free.<br>


### 3.3. Browser Plugins
There are a billion browser plugins out there that claim to provide security. However, they come with the same issues as many VPNs—you're trusting a 3rd party (often a single developer) to protect you.<br>
Secondly, part of browser fingerprinting involves which and how many plugins you have, so the more you install, the more unique your browser's fingerprint is.<br>
Now, I'm not shitting on browser plugins; in fact, I'm going to cover some in-depth later on. But for now, there are a couple that do what they say on the label, and are worth noting here:<br>

- [AdNauseam](https://adnauseam.io/) — AdNauseam incorporates [uBlock Origin](https://ublockorigin.com/) and, alongside blocking ads, it clicks all of them.
- [Random User-Agent](https://github.com/tarampampam/random-user-agent) — This addon randomizes your browser's user-agent and changes it every few minutes.


## 4. Evaluating Potential Threats

Some of the assets and adversaries may stand out to you as particularly important. Which ones will depend on your personal threat model, and will vary from person to person.<br>
If you're an activist or journalist, then maybe you're most worried about governments knowing your realtime location.<br>
If you're a female college student, then maybe you're worried about a stranger or another classmate knowing your dorm room and when you're away for your night class.<br>
Perhaps you're a member of a marginalized community, like the LGBTQIA+, and you don't want to be outed to family or co-workers.<br>

Each of these require different considerations when managing your online presence and the data it leaves behind.<br>


## 5. Determining the Impact

Assess the potential impact for each identified threat. Consider the severity of the fallout if the adversary had access to specific PII or BD.<br>


## 6. Plan for Risk Mitigation

After identifying the risks and evaluating the impact, the next step is planning for risk mitigation. This involves selecting and prioritizing the measures or controls to reduce the risk of threats.<br>


## 7. Regular Review and Update 

Threat modeling is not a one-time process. You should routinely review and update your model to account for new assets, threats, and vulnerabilities.<br>

---

# Part II: Making Noise (ROUGH DRAFT W/ PLACEHOLDER TEXT)

Now that we've set the stage and established our threat model, it's time to take some action.<br>
In this section, we'll explore different strategies that you can use to make noise and pollute your data online.<br>
By doing so, you can make it harder for adversaries to gather accurate information about you.<br>


## 1. Old and Alternatives Accounts

One strategy is to create alternative accounts for various online platforms. This can help you segregate aspects of your life and provide an additional layer of privacy.<br>
By using different usernames, email addresses, and other identifying information, you can make it harder for adversaries to link your online activities together.<br>

You can lower your attack surface and add noise by logging into old accounts you don't use anymore, and replacing accurate information in them with both plausible and obvious misinformation.<br>
Wait a while, or request some search engines to reindex that page, then delete the account once the misinformation shows up in search results.<br>


## 2. Opting Out

Many data brokers and online platforms provide an opt-out option that allows you to remove or limit the amount of personal information that they collect and share.<br>
Don't forget to "update" your information first.


## 3. Disinformation

Another strategy to pollute your data is by intentionally sharing false or misleading information online.<br>
By mixing in inaccurate details about your personal life, interests, or demographics, you can create noise and make it harder for adversaries to discern the truth.<br>


## 4. Automated Fuckery

Automation can be a powerful tool to pollute your data online. By utilizing scripts, bots, or browser extensions, you can automate actions such as web browsing, social media activity, or search queries.<br>
This can help create noise and generate data that may not accurately reflect your actual behavior or interests.<br>


## 5. Behavioral Changes

Lastly, consider making intentional behavioral changes to limit the amount of personal information you share online.<br>
For example, you can reduce your reliance on social media platforms, avoid oversharing personal details, and carefully consider the privacy settings of the apps and services you use.<br>
By being mindful of your digital footprint and being selective about the information you disclose, you can actively protect your data privacy.<br>

---
