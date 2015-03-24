solrCoreManager
===============

Some scripts to manage Solr multicore support for Solr 1.4 on Ubuntu servers. 

Original scripts written by Dustin Rue (http://blog.dustinrue.com/archives/690). If you're interested in Solr Multicore on Solr 3.4, check out http://blog.dustinrue.com/archives/927

Moved here as I use them a lot and keep losing my bookmarks. The following instructions are mostly taken from this blog post as well.

Assumptions
-----------
The following is assumed about your server environment. If you use these script on a different flavour of *NIX, your mileage might vary.

1. The server is Ubuntu 10.04 or later;
2. You installed Solr from the default repositories; and
3. The version of Solr is 1.4.


Getting Started
---------------

Download all the scripts to a suitable place on your server, and make sure they're all executable.

Create a file called `solr.xml` in `/usr/share/solr` and add the following code.

```
<solr persistent="true" sharedLib="lib">
  <cores adminPath="/admin/cores">
 </cores>
</solr>
```

Update the permissions for this file and the containing folder.

```
chown tomcat6.tomcat6 /usr/share/solr/solr.xml
chown tomcat6.tomcat6 /usr/share/solr
```

Then restart Tomcat.

Managing Cores
--------------

Create a template directory
```
cp -av /etc/solr/conf /etc/solr/conftemplate
```

Next, edit `/etc/solr/conftemplate/solrconfig.xml` and change dataDir to
```
<dataDir>/var/lib/solr/data/CORENAME</dataDir>
```

This will allow the scripts to run properly.

You can now use the scripts to manage cores on your Solr server.
