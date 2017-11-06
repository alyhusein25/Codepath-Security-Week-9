# Codepath-Security-Week-9


# Honepots Deployed

I deployed the dionaea honeypot using the MHN application. 


# Issues Encountered

The deployment of this honeypot was fairly straight forward. I did have to go through the instructions a couple of times because I had never used the Google Cloud platform before. The online VM management system was pretty tricky to get around initially, but after a few minutes it was pretty easy to redeploy the machines and edit settings. The firewall settings were also confusing at first because of the "http-server" setting. It was enabled through the command line, but whenever I went to the web console it showed as disabled. So I had to disable and enable it manually. The nginx server the application was running behind did crash a few times on me and gave 504 errors. Those, however, were resolved automatically after a couple of minutes. 


# Data

I deployed the application on Monday 10/30/2017. By Sunday, 11/5/17 there were 28,314 attack attempts on the application. Most of these attacks seemed to have come from the U.S and China. Though there were also a significant amount of Canada, Japan, Netherlands, Brazil, and India. Using python, I did some basic analysis and found the top 5 protocols for the attacks were, in order:

* pcap: 22549
* SipSession: 1468
* smbd: 680
* mysqld: 544
* httpd: 539


The top 5 destination ports were, in order:

* 23: 3245
* 5060: 1897
* 445: 682
* 3306: 544
* 80: 539

It is interesting seeing port 23 was the most common port to attack. Telnet makes a bit of sense as no one really uses it anymore. However, most people may not patch the service, so it could be an easy exploit. 3306 and 80 make sense to be in the top 5 as both of those are common ports and services mistakenly open on servers. 5060 was also interesting to see. This port is used for plain-text Session Initiation Protocol (SIP). The SIP protocol is for things like VoIP.

The top 5 source ip addresses were, in order:

* 64.71.137.106: 16432
* 192.99.14.190: 1089
* 61.178.176.27: 253
* 73.31.151.69 : 249
* 158.69.241.18: 183

Using a basic IP lookup website, the top IP was reported to come from California. The second most common IP came from Canada. 


# Questions

In the previous section I a bit of confidence that most of the attacks came from US and China, however, I am not 100% in that statement. As show by the IP addresses the top 2 countries were US and Canada (but that doesn't necessarily count other unique addresses from the same country). I was hoping the exported JSON would have the origin country as part of each object, but it did not. 
