# Overview

These are the tests used to validate images before being released to the Joyent Public Cloud.

These tests are are based on [Serverspec](http://serverspec.org) "Serverspec.org").

## Installation and Setup

To run the tests you will need ruby (1.9.3+ or 2.0.0 should work) and rubygems installed.

Install serverspec with

    gem install serverspec

Copy the `properties_example.yml` file to `properties.yml`

Modify `properties.yml` with the name and properties you want to test. 

Next, edit your `~/.ssh/config` file with the host information of the virtual machines you want to test. The name you chose for _Host_ in `~/.ssh/config` should match what you have in `properties.yml`. 

For example, here's a `properties.yml` file:

    debian-7:
      :roles:
        - debian
      :name: Debian 7.8 (wheezy)
      :version: 20150128
      :doc_url: https://docs.joyent.com/images/linux/debian

And an example `~/.ssh/config` file:

    Host debian-7
      HostName xxx.xxx.xxx.xx 
      User root

## Running the tests

To run the tests, run the following command (within this directory):

    rake serverspec

Or just:

    rake

More information on how to create serverspec tests can be found here:

http://serverspec.org/tutorial.html

There's a list of useful Resource Types here that you can use for testing:

http://serverspec.org/resource_types.html
