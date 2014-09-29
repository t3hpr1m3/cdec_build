# Building CDEC

## Prerequisites

You will need the following Vagrant plugins installed:

1.  vagrant-berkshelf
2.  vagrant-omnibus
3.  vagrant-vbguest
4.  vagrant-cachier (optional, but recommended)

## Building

1.  Download and build [Boost](http://www.boost.org/)

    ```shell
    # /vagrant/cdec_root/bin/cdec_env /vagrant/build_boost
    ```

2.  Download and build [cdec](http://www.cdec-decoder.org/)

    ```shell
    # /vagrant/cdec_root/bin/cdec_env /vagrant/build_cdec
    ```

## Packaging

The entire cdec suite (including Boost) should now be contained in
`/vagrant/cdec_root`, and can be archived, copied to another location.

Just make sure that you wrap calls to any of the cdec tools are wrapped
in `cdec_env`, as in:

`# /vagrant/cdec_root/bin/cdec_env /vagrant/cdec_root/bin/cdec --help`
