# Amazon ElastiCache Cluster Configuration for .NET

Amazon ElastiCache Cluster Configuration is an enhanced .NET library that supports connecting to an Amazon ElastiCache cluster for Auto Discovery. This client library is an extension built upon Enyim and is released under the [Apache 2.0 License](http://aws.amazon.com/apache2.0/).

## Usage

To use Amazon ElastiCache with Auto Discovery, the ElastiCacheClusterConfig object must be passed to the MemcachedClient object. An ElastiCacheClusterConfig can be created from the App.config if there is a clusterclient section or you can pass a different section.

	var client = new MemcachedClient(new ElastiCacheClusterConfig());

ElastiCacheClusterConfig can also be instantiated by providing it an AutoConfigSetup or simply provide the hostname and port like so:

	var client = new MemcachedClient(new ElastiCacheClusterConfig("hostname", 11211));

Once instantiation occurs in this way, MemcachedClient can be used the same way as the [Enyim Client](https://github.com/enyim/EnyimMemcached). The only difference is a background process polls the cluster and updates nodes when changes occur.

## App.config
To configure the AutoClient from app.config the section "clusterclient" or the specified section must have an endpoint that contains a hostname and port specified as so:

    <endpoint hostname="clusterclient.4mpstz.cfg.use1.cache.amazonaws.com" port="11211" />

There are also optional regions as shown below:

    <node nodeTries="5" nodeDelay="1000" />
    <poller intervalDelay="60000" />

These settings as well as all the settings included in Enyim can be configured through the app.config as seen [here](https://github.com/enyim/EnyimMemcached/wiki/MemcachedClient-Configuration#appconfig).

## Enyim Client
Because this binary is used as a configuration object for the Enyim MemcachedClient, usage beyond instantiation is all exactly the same so refer to [this wiki](https://github.com/enyim/EnyimMemcached/wiki) or [this google group](https://groups.google.com/forum/#!forum/enyim-memcached) on how to use the actual client.

## Wiki
The wiki found [here](https://github.com/awslabs/elasticache-cluster-config-net/wiki) goes into more detail on the usage of the ElastiCacheClusterConfig object as well as how the project takes advantage of Auto Discovery.

## Requirements

You'll need .NET Framework 3.5 or later to use the precompiled binaries. To build the client, you'll need Visual Studio 2010 or higher.