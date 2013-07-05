solrCoreManager
===============

Some scripts to manage Solr multicore support for Solr 1.4

Original scripts written by Dustin Rue (http://blog.dustinrue.com/archives/690). If you're interested in SOlr Multicore on Solr 3.4, check out http://blog.dustinrue.com/archives/927

Moved here as I use them a lot and keep losing my bookmarks. The following instructions are mostly taken from this blog post as well.

Getting Started
---------------

Create a file called `solr.xml` in `/usr/share/solr` add the following

```
<solr persistent="true" sharedLib="lib">
  <cores adminPath="/admin/cores">
 </cores>
</solr>
```

Update the permissions for this file and the containing folder

```
chown tomcat6.tomcat6 /usr/share/solr/solr.xml
chown tomcat6.tomcat6 /usr/share/solr
```

and restart Tomcat.

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
