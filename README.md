# Ansible Role: Android SDK

An Ansible Role that installs the Android SDK tools, SDK packages and dependencies on Ubuntu.

## Requirements

A recent version of Ubuntu.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    android_sdk_download_location: http://dl.google.com/android/android-sdk_r23.0.2-linux.tgz

The location to the Android SDK tools package to be installed.

    android_sdk_install_location: /opt

The location on disk where you'd like to SDK to be installed.

    android_sdk_dependency_packages:
  		- "libncurses5"
		- "libstdc++6"
		- "zlib1g"
		- "imagemagick"
		- "expect"
		- "gradle"
		- "ant"
		- "ccache"
		- "autoconf"
		- "automake"
		- "ccache"
		- "python-dev"
		- "zlibc"

A list of aptitude installable build dependency packages.

    android_sdks_to_install: "build-tools-20.0.0,build-tools-19.1.0,platform-tools,tools,android-21,android-20,android-19,android-18,android-17,android-16,extra-android-support,extra-google-m2repository,extra-android-m2repository"

The actual Android SDK packages to install using the SDK manager.

## Example Playbook

    - hosts: appbuild
      vars_files:
        - vars/main.yml
      roles:
        - { role: nickp666.android-sdk }

## License

BSD

## Author Information

This role was created in 2015 by [Nick Pack](https://github.com/nickpack).

## Contributers

* @edunham - Fixed 32bit support
