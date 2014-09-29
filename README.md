# Building CDEC

## Prerequisites

You will need the following Vagrant plugins installed:

1.  vagrant-berkshelf
2.  vagrant-omnibus
3.  vagrant-vbguest
4.  vagrant-cachier (optional, but recommended)

## Building

1.  Bootstrap the build environment

    ```shell
	$ /vagrant/bootstrap
	```

2.  Download and build [Boost](http://www.boost.org/):

    ```shell
    $ /vagrant/cdec_root/bin/cdec_env /vagrant/build_boost
    ```

3.  Download and build [cdec](http://www.cdec-decoder.org/):

    ```shell
    $ /vagrant/cdec_root/bin/cdec_env /vagrant/build_cdec
    ```

## Packaging

The entire cdec suite (including Boost) should now be contained in
`/vagrant/cdec_root`, and can be zipped up and copied to a different
location.  The caveat is that any calls to executables in the cdec
suite will need to be wrapped in a call to `cdec_env`:

```shell
# /path/to/cdec/bin/cdec_env /path/to/cdec/bin/fast_align --help
```

