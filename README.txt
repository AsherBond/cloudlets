cloudlets v.0.0.4

Author: Solomon Hykes <solomon.hykes@dotcloud.com>
License : see LICENSE file.
Url: http://bitbucket.org/dotcloud/cloudlets

Description:
------------

Cloudlets are universal server images for the cloud.

They're lightweight, version-controlled, and you can export them to any bootable format known to man: Xen, KVM, Amazon EC2, or just a plain bootable CD.


Installing:
-----------

1. One of our dependencies (python-spidermonkey) requires the following system packages to be installed:

    On Ubuntu/debian:
    # apt-get install pkg-config build-essential python-dev libspr4-dev

2. Run the install script

    # python setup.py install


Examples:
---------

# cloudlets find sample.cloudlet

    List the contents of an image

# cloudlets find sample.cloudlet --only templates volatile

    List only template and volatile files in an image

# cloudlets manifest sample.cloudlet

    Display an image's manifest

# cloudlets tar sample.cloudlet --config '{"args": {"hostname": "host1"}, "dns": {"nameservers": ["0.0.0.0"]}, "ip": {"interfaces": []}}' | tar tv

    Generate a tar archive from an image, configuring it on the fly with the given JSON configuration.
    The tarball can be piped into vm2vm [1] to generate an EC2 image, for example.

[1] http://bitbucket.org/dotcloud/vm2vm

# touch sample.cloudlet/etc/foo
# cloudlets hg sample.cloudlet add
# cloudlets hg sample.cloudlet commit -u "Solomon Hykes <solomon.hykes@dotcloud.com>" -m "Added configuration file foo"

    Make a change to an image, then commit it using Mercurial.


Coming soon:
------------

 * Distributed versioning (fork and improve other people's images!)
 * Multi-image stacks
 * Automated tests (Cucumber tests for your stack!)
 * VM generator

And much more.
