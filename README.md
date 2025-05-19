Framework for Rogue Wi-Fi Access Point Attack

Description
WiFi-Pumpkin is a security tool that provides the Rogue access point to Man-In-The-Middle and network attacks.

Installation
Kali 2.0/WifiSlax 4.11.1/Parrot 2.0.5

Python 2.7
 git clone https://github.com/P0cL4bs/WiFi-Pumpkin.git
 cd WiFi-Pumpkin
 chmod +x installer.sh
 ./installer.sh --install
refer to the wiki for Installation

Features
Rogue Wi-Fi Access Point
Deauth Attack Clients AP
Probe Request Monitor
DHCP Starvation Attack
Credentials Monitor
Transparent Proxy
Windows Update Attack
Phishing Manager
Partial Bypass HSTS protocol
Support beef hook
Mac Changer
ARP Poison
DNS Spoof
Plugins
Plugin	Description
net-creds	Sniff passwords and hashes from an interface or pcap file
dns2proxy	This tools offer a different features for post-explotation once you change the DNS server to a Victim.
sslstrip2	Sslstrip is a MITM tool that implements Moxie Marlinspike's SSL stripping attacks based version fork @LeonardoNve/@xtr4nge.
sergio-proxy	Sergio Proxy (a Super Effective Recorder of Gathered Inputs and Outputs) is an HTTP proxy that was written in Python for the Twisted framework.
Transparent Proxy
Transparent proxies that you can use to intercept and manipulate HTTP/HTTPS traffic modifying requests and responses, that allow to inject javascripts into the targets visited. You can easily implement a module to inject data into pages creating a python file in directory "Proxy" automatically will be listed on PumpProxy tab.

Plugins Example
The following is a sample module that injects some contents into the tag to set blur filter into body html page:

from Plugin import PluginProxy

class blurpage(PluginProxy):
   ''' this module proxy set blur into body page html response'''
   _name          = 'blur_page'
   _activated     = False
   _instance      = None
   _requiresArgs  = False

   @staticmethod
   def getInstance():
       if blurpage._instance is None:
           blurpage._instance = blurpage()
       return blurpage._instance

   def __init__(self):
       self.LoggerInjector()
       self.injection_code = []

   def setInjectionCode(self, code):
       self.injection_code.append(code)

   def inject(self, data, url):
       injection_code = '''<head> <style type="text/css">
       body{
   	filter: blur(2px);
   	-webkit-filter: blur(2px);}
   	</style>'''
       self.logging.info("Injected: %s" % (url))
       return data.replace('<head>',injection_code )
Screenshots
Screenshot on the wiki

FAQ
I can't install it

have a look at the Installation

I have this message warning Error Network Card

You system not have support run Wifi-Pumpkin with Wireless connection

hi , is it work on X Wireless Adapters ?

I don't know, check this page

I can't install package X

Try installing the package via pip, Google is your friend!

It Windows supported?

No, It will never be

Contact Us
Whether you want to report a bug, send a patch or give some suggestions on this package, drop us or open pull requests

Happy MITM!
