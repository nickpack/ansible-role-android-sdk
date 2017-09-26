# Ansible Role: Android SDK

[![Build Status](https://travis-ci.org/nickpack/ansible-role-android-sdk.svg?branch=master)](https://travis-ci.org/nickpack/ansible-role-android-sdk)

An Ansible Role that installs the Android SDK tools, SDK packages and dependencies on Ubuntu and RedHat based OS'.

## Requirements

A recent version of Ubuntu.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    android_sdk_download_location: http://dl.google.com/android/android-sdk_r23.0.2-linux.tgz

The location to the Android SDK tools package to be installed.

    android_sdk_install_location: /opt

The location on disk where you'd like to SDK to be installed.

    ubuntu_dependency_packages:
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
      - "ant"
      - "ccache"
      - "python-dev"
      - "zlibc"

A list of aptitude installable build dependency packages.

    ubuntu_precise_dependency_packages:
      - "libgd2-xpm"
      - "libgphoto2-2"
      - "libsane"
      - "ia32-libs-multiarch"

A list of aptitude installable build dependencies for Ubuntu Precise.

    rh_dependency_packages:
      - expect
      - libstdc++.i686
      - mesa-libGL-devel
      - ncurses-libs.i686
      - zlib.i686

A list of yum installable build dependencies for RedHat based OS.

    android_sdk_update_path: true

Whether or not the role should update the PATH in /etc/environment with the relevant android SDK locations

    android_sdk_base_buildtools_version: 20.0.0

The main build tools version from the SDK to use, mainly useful for PATH updates.

    android_sdk_tools_to_install:
      - build-tools-20.0.0
      - build-tools-19.1.0
      - platform-tools
      - tools
      - extra-android-support
      - extra-google-m2repository
      - extra-android-m2repository
    android_sdks_to_install:
      - android-21
      - android-20
      - android-19
      - android-18
      - android-17
      - android-16

The actual Android SDK packages to install using the SDK manager.

## Example Playbook

    - hosts: appbuild
      vars_files:
        - vars/main.yml
      roles:
        - { role: nickpack.android-sdk }

## License

BSD

## Author Information

This role was created in 2015 by [Nick Pack](https://github.com/nickpack).

## Contributors

* @timdaman - Fixed defect in variable loading
* @ojechev-broadsoft - OSX Support
* @rodrigdav - Fixed bare variables that broke 2.2 compatibility
* @halkeye - Seperated SDK tools, fixed 64bit environment
* @edunham - Fixed 32bit support
* @peterjanes - Added RedHat family support
* @conorsch - Changed conditionals to allow > 14.04 support
