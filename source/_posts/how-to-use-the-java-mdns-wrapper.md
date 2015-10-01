title: How To use the Java mDNS Wrapper
tags:
  - apple
  - bonjour
  - dns service discovery
  - dns-sd
  - java
  - jmdns
  - mdns
  - mdnsresponder
  - zeroconf
id: 65
categories:
  - Tech
date: 2008-01-10 17:21:25
---

A few days ago I[ posted an article](http://www.offthehill.org/articles/2008/01/08/a-jmdns-mdnsresponder-zeroconf-compatibility-interface/) about my wrapper API which unifies the mDNSResponder and JmDNS packages behind a single interface, but I neglected to provide usage examples or a usage guide. I'll try and correct that now.

In addition to unifying multiple mDNS implementations under a single API, I think my API reduces the amount of work needed by the developer for registering and listening for services to a minimum.

**Building the code**
First off, all you should need to  compile and run my package is [Maven](http://maven.apache.org). Once you have Maven installed, cd into the jmdns directory, and run:

`mvn test`

This will compile JmDNS, my add-on API, and run a few unit tests. The API in question is tested by `org.jmdns.api.DiscoveryFactoryTest`. I would expect the JmDNS portion of the test `testJmDNS()` to pass under almost any circumstance, but the `testmDNSResponder()` will only pass if you are running on Linux and have mDNSResponder (or possibly the avahi compatibility layer) installed successfully.

**Example usage - Initialization**

Before registering or listening for services, you need to initialize the discovery subsystem:

`DiscoveryFactory.initRegistry(
DiscoveryFactory.DISCOVERY_REGISTRY_DEFAULT);`

The above will use the default mDNS implementation (JmDNS). Alternatively you can use the following to use JmDNS explicitly:

`DiscoveryFactory.initRegistry(
DiscoveryFactory.DISCOVERY_REGISTRY_JMDNS);`

Or mDNSResponder instead:

`DiscoveryFactory.initRegistry(
DiscoveryFactory.DISCOVERY_REGISTRY_MDNSRESPONDER);`

Consider this an initialization a singleton, you should do this once and only once per JVM instance.

**Example usage - Registering a Service**

Assuming the system is initialized, the following code will register a service:

`HashMap<string,> props = new HashMap<string,>();
props.put("type", "website");</string,></string,>`

`IDiscoveryRegistry registry = DiscoveryFactory.getRegistry();`

`IServiceInfo myService = registry.registerService("_http._tcp", "mySite", null, 80, props);
`

Note the 'null' in the registerService() call is to use the default domain (.local). You can pass a domain name here to register in another domain.

To unregister your service, just do:

`registry.unregisterService(myService);`

**Example usage - Listening for a Service**

Create a listener:

`BaseDiscoveryListener listener = new BaseDiscoveryListener("_http._tcp", "website", null);`

Wait 15 seconds for a service:

`listener.waitForFirstService(15000);`

Get the first service found:

`IServiceInfo service = listener.getFirstService();`

Print out some information on the service:

`System.out.println("service name: " + service.getName() + " at " + service.getHostAddress() + ", port: " + service.getPort());`
