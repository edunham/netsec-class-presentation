===========================
Network Penetration Testing
===========================

**"Don't giggle, we're all grownups here"**

|

(Mike said we needed a provocative title)

What's pentesting? 
==================

.. note:: emily
|
.. figure:: _static/whitehat_blackhat.jpg
    :align: center

* Legally searching a system for security vulnerabilities

.. note:: Penetration Testing -- Find prospective vulnerabilities and then
    verify that an attacker could exploit them
    
    Includes automatic or manual vulnerability scans plus other techniques

    * Targeted testing -- whitebox, cooperative with internal teams
    * External testing -- Done from outside the network
        * Misses what if attacker is a company insider
        * How far could a malicious external party break in?
    * Internal testing -- Simulate disgruntled employee w/ standard access
        * Disgruntled sysadmin? You're out of luck
    * Blind testing -- black-box
        * Only have company name + any tech blogs / logs about infra
    * Double Blind testing -- most of company isn't aware of test
        * Makes social engineering techniques more effective

    (from http://searchsoftwarequality.techtarget.com/definition/penetration-testing) 

Getting into the industry
=========================

.. note:: Dean. Getting into the pen-testing / the computer security focused 
          industry is not too difficult. It used to be that many 'hackers'
          as portrayed by the media were black-hat, and often got into the
          industry by breaking systems without permission. Since then,
          there have been many improvements to our current systems of 
          reporting bugs without getting in trouble, such as bug bounties.
          This allows people to try and find security vulnerabilities in 
          applications such as Facebook, Google, etc. and report them for
          a monetary reward. Before, people may try and break systems and
          instead of being rewarded, be attacked by the industry for finding
          the bugs without permission in the first place. Other ways of getting
          into industry are getting certifications, proving you know what
          you're doing. However, getting real clients, or getting involved with
          a good consulting company usually requires more than just certification;
          experience is the most valuable.

.. figure:: _static/hacker.jpg
    :align: center
    :scale: 50%

* Often background in black-hat work
* Certifications/degrees can help; experience counts most
* CTFs
* Bug bounties

Pentesting Clients
==================
|
.. note:: emily

.. figure:: _static/magnifying_glass_on_password.jpg
    :align: center
    :scale: 60%

* Anyone whose systems might be attacked
    * Banking
    * e-commerce
    * Governments
    * Corporations
    * Military

.. note:: Anyone who has a large software deployment in the wild and might
    face malicious intruders needs it

    Any company building/selling product with security claims, ie firewall
    or operating system code, also needs to audit and rigorously test
    deployments of their product

    Also open source projects related to network security (ie Tomato the
    router firmware) really ought to pentest themselves.


How can pentesting be done legally?
===================================

.. note:: dean
          Check with site owners, or look for a bug bounty program.
          Check acceptable use poliicies!! Do not want to get in trouble for
          not reading the fine print. 
          When reporting issues, be sure to thoroughly explain your processes.
          1. General summary of what the bug is.
          2. Give a clear definition of the steps to repeat to make the bug
             happen again.
          3. Explain what the meaning of the bug is. How can it compromise a
             a system.
          4. Explain ways to fix the bug. 

          Most of all, be sure to disclose the bug to the company first,
          and give ample time for the company to respond to your original
          disclosure before disclosing the bug to public (especially if it
          discloses sensitive information).

.. figure:: _static/bugbounty.png
    :align: right
    :scale: 50%

* Contract with owner of system
    * Legal consent to find vulnerabilities
    * Clear explanation of what may be done with discovered problems
    * Avoid breaking laws about disclosing sensitive data
* Some companies offer bug bounties, reporting programs

Acceptable Use Policies
=======================

.. note:: emily

**Authorized Use**

.. figure:: _static/osu_aup.png
    :align: center

.. note:: There's always that clause 

    Entry into a system, including the network system,
    by individuals not specifically authorized (by
    group or personally) or attempts to circumvent the
    protective mechanisms of any University
    system are prohibited.
    (http://oregonstate.edu/senate/agen/2006/aupcurrent.pdf)

    **All users of University computing resources must**

    Use only those computing resources that they are authorized to use and use
    them only in the manner and to the extent authorized.

    Refrain from unauthorized attempts to circumvent the security mechanisms
    of any University system.

    When using University computing resources to access non-University
    resources, observe the acceptable use policies of those non-University
    organizations

    from http://oregonstate.edu/fa/manuals/gen/computing-resources

Acceptable Use Policies
-----------------------

.. figure:: _static/aws.png
    :align: center

.. note:: emily    | **AMAZON**

    Says that because penetration is "frequently indistinguishable from"
    security violations & network abuse, one needs permission

    https://aws.amazon.com/security/penetration-testing/

    Permission is required for all penetration tests.

    To request permission, you must be logged into the AWS portal

    (& restrictions on instance types from which you can pentest)


Tools & Techniques
==================
|
.. figure:: _static/toolbag.jpg
    :align: center

Metasploit
----------


* Metasploit framework
* Free & Open Source
* Includes anti-forensic and evasion tools
* Choose exploit, encoding, and payload, then execute
  
.. figure:: _static/metasploit_logo.png
    :align: center

.. note:: Emily 
    
    Choosing and configuring an exploit (code that enters a target system by
    taking advantage of one of its bugs; about 900 different exploits for Windows,
    Unix/Linux and Mac OS X systems are included);
    
    Optionally checking whether the intended target system is susceptible to 
    the chosen exploit;

    Choosing and configuring a payload (code that will be executed on the 
    target system upon successful entry; for instance, a remote shell or a 
    VNC server);
    
    Choosing the encoding technique so that the intrusion-prevention system 
    (IPS) ignores the encoded payload;
    
    Executing the exploit.

    **Need some info about OS and network config to choose correct payload**

nmap
----

.. note:: Dean, with example. nmap is a very powerful tool. Most of the
          features it provides help assess the vulnerability of networks.
          Some of these include:
          1. What computers did you find running on the local network?
          2. What IP addresses did you find running on the local network?
          3. What is the operating system of your target machine?
          4. Find out what ports are open on the machine that you just scanned?
          5. Find out if the system is infected with malware or virus.
          6. Search for unauthorized servers or network service on your network.
          7. Find and remove computers which don't meet the organization's minimum level of security.

* Network sweeps
* network tracing
* port scans
* OS fingerprinting
* version scans
* vulnerability scans

nmap
----

.. figure:: _static/nmap_example.png
    :align: center

Nessus
------

.. note:: dean 
    long story short it's proprietary and mainly works on size of
    vulnerability databse
 Dean. Nessus is a network scanning utility. It integrates with
          nmap for increased coverage, as well as Hydra (a weak password
          tester) and Nitko ( a cgi/.scripts checker) You can check for
          misconfigurations DoS your websites, check for passwords, and more. 

* Proprietary, integrated vulnerability scanner
* 2.2.11 and before were GPL
* Misconfiguration, DoS with mangled packets, default passwords, PCI DSS audit
    * (Payment Card Industry Data Security Standard)

.. figure:: _static/nessus.png
    :align: center

Wireshark
---------
|
.. note:: dean
    Use Wireshark to find weak networks

    * Device (almost) always has same MAC (Media Access Control address)
        * Use this to see who's who across networks, correlate person to IP
    * Catch authentication handshakes for some protocols (replay attacks)
    * Fingerprint operating systems (sometimes down to browser version if
      unsecured network) to figure out what attacks to use
     Dean. You can look for secured network points and wait for people
      to make unencrypted requests to the router for passwords to log in.

      Additionally, you may 'sniff' other unencrypted (or insecurely
      encrypted) passwords from when people are logging in websites and
      whatnot. Basically, Wireshark gives you the ability to look at
      everything traveling between networks in a close radius to yourself.

.. figure:: _static/wireshark.png
    :align: center

* Unsecured access points
* Mis-configured networks can leave passwords visible

Social engineering
------------------

.. note:: emily

.. figure:: _static/kid_dressed_as_pilot.jpg
    :align: right
    :scale: 60%

* Pretexting
* Phishing (& "spear phishing")
* Baiting
    * Stuxnet
* Quid pro quo
* Tailgaiting

Vulnerabilities
===============

* SQL injection

.. note:: Dean: We have discussed many of these previously, but here is another
          recap of what each of the exploits are and how to exploit them.
    ' or 1=1; -- for strings, or 1=1; -- for not strings. (select statements)

* XSS

.. note:: Link a script that you input, in a section that may be rendered by
          unknowing users. (Hint: Comments!)

* CSRF

.. note:: Use someone else's validated session to perform actions on their
          behalf without their knowing of it.

Clueless (l)users
-----------------

.. note:: emily

    * Password reuse 
        * Bad passwords
        * Writing them down
    * Lost devices
        * VPN access
        * Email
        * Saved passwords
    * Failure to log out / lock screen
    * Disgruntled employees


.. figure:: _static/bad_at_computer.jpg
    :align: right

* Password reuse 
    * Bad passwords
    * Writing them down
* Lost devices
    * VPN access
    * Email
    * Saved passwords
* Failure to log out / lock screen
* Disgruntled employees

Known, unpatched vulnerabilities
--------------------------------

.. note:: dean, & focusing on networking hardware / routers.
    Some of the biggest exploits in history usually take advantage of known
    unpatched vulnerabilities on the host systems.  
    
    Bottom image is from https://zmap.io/heartbleed/ and is "Historical
    Trend of Vulnerable HTTPS Enabled Alexa Top 1 Million Websites"


.. figure:: _static/heartbleed.jpg
    :align: right
    :scale: 60%

* OS vulnerabilities

.. note:: 
    Vertical privilege escalation requires the attacker to grant himself
    higher privileges.

     Horizontal privilege escalation requires the attacker to use the same level
     of privileges he already has been granted, but assume the identity of another
     user with similar privileges. 
    (http://searchsecurity.techtarget.com/definition/privilege-escalation-attack)

    When attacking Unix systems, look for writable set UID files, unmounted
    filesystems, dev tools...



.. note:: insecure file creation vulnerability. A broken application may try to
          create a temporary file in a public writeable directory (e. g. /tmp) 
          without forcing create-only. The attacker will create a symlink 
          pointing elsewhere (where the attacker does not have write 
          permission). The vulnerable application will overwrite the target 
          file (e. g. /home/someuser/.profile for normal users and a system file for root).

* Web server vulnerabilities

.. note:: Heartbleed; what it is, how it works briefly.
          What: Heartbleed allows you to send a vulnerable server some data,
                but if you ask for more bytes back than what you send as
                your first message, you'll start reading from RAM! This
                can expose anything in memory: private keys, certs, look
                at encrypted data from other connected users.

* Web development frameworks

.. note:: Your web development frameworks, that interact with web servers
          can also be vulnerable. A recent vulnerability in the common Ruby
          on Rails web framework could potentially allow an attacker to malform
          a dynamic directory for a file to render, and instead point somewhere
          else. This is an input sanitization issue.

.. figure:: _static/heartbleed_vulns.png
    :align: center

Scroll down on https://zmap.io/heartbleed/ for a list of sites still
vulnerable

Ethical Issues
==============

.. note:: emily

* Disclosing user data
* Discovering confidential data
* Appropriate disclosure if client doesn't fix vulnerabilities
    * Unfixed problems can endanger client's users
* Destructive vs. non-destructive testing
    * DoS attacks impact users, but would be available to malicious intruders

Results of pentesting
=====================

* CVEs
* Security reports
    * Threat level modeling
* Possible impact on users
    * DoS
    * Disclosure if vulnerability could have silently leaked private data
        * heartbleed

.. note:: emily 
    Who would discover that a vulnerability had been exploited? (pentester, DBA, sysadmins, etc.)

    CVE = Common Vulnerability Exposure

    http://nvd.nist.gov/

    How would the pentester's results be presented?

    What actions would be taken by the company as a result?


