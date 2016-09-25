+++
author = "osgav"
date = "2016-09-25T11:37:09Z"
draft = true
image = "images/rundeck-logo2.png"
share = true
slug = "rundeck-cloudformation"
title = "Rundeck CloudFormation"

+++

[< back to projects](/page/projects)<br />
**`created: 25/09/2016`**

---

A basic CloudFormation template for spinning up an EC2 instance and installing Rundeck on it. 

This CloudFormation template simply installs Rundeck as per the instructions from their website. No further configuration is applied. You will end up with a basic Rundeck installation which you can log into with default credentials.

Only a handful of changes were made to AWS' CloudFormation template for a [basic LAMP stack](https://s3-us-west-2.amazonaws.com/cloudformation-templates-us-west-2/LAMP_Single_Instance.template) - they are as follows:

```
> one: blah blah exyz
>

```

```
> two: blah blah zyxe
>

```



Taking the [example CloudFormation](https://aws.amazon.com/cloudformation/aws-cloudformation-templates/) for a [basic LAMP stack](https://s3-us-west-2.amazonaws.com/cloudformation-templates-us-west-2/LAMP_Single_Instance.template), I was able to make a few simple changes to have it install Rundeck instead and return the URL to access Rundeck in its Output.




[Hugo Build and Publish Workflow](/page/projects/hugo-build-and-publish-workflow)<br />
[Hugo Markdown Cheatsheet](/page/projects/hugo-markdown-cheatsheet)

> download source and website --><br />

```
> HTTPS authentication until I set up SSH authentication
> Run from vagrant virtual machine at /vagrant/workbench
$ git clone https://osgav@github.com/osgav/osgav-source.git osgav-source
$ git clone https://osgav@github.com/osgav/osgav.github.io.git osgav-root-public
```

> view cheatsheet --><br />

```
$ cd osgav-source
$ ./hugo/01-serve-withdrafts
> view blog in browser at http://192.168.56.2:1313 - cheatsheet is latest post
```



