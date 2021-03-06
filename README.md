Terraform Provider
==================

- Website: <https://www.terraform.io>
- [![Gitter chat](https://badges.gitter.im/hashicorp-terraform/Lobby.png)](https://gitter.im/hashicorp-terraform/Lobby)
- Mailing list: [Google Groups](http://groups.google.com/group/terraform-tool)

<img src="https://cdn.rawgit.com/hashicorp/terraform-website/master/content/source/assets/images/logo-hashicorp.svg" width="600px">

Maintainers
-----------

This work-in-progress provider plugin is maintained by the Marques Johansson (for now).

Requirements
------------

- [Terraform](https://www.terraform.io/downloads.html) 0.10.x
- [Go](https://golang.org/doc/install) 1.8 (to build the provider plugin)

Usage
---------------------

```tf
# For example, restrict linode version in 0.1.x
provider "linode" {
  version = "~> 0.1"
}
```

Building The Provider
---------------------

Clone repository to: `$GOPATH/src/github.com/terraform-providers/terraform-provider-linode`

```sh
mkdir -p $GOPATH/src/github.com/terraform-providers
cd $GOPATH/src/github.com/terraform-providers
git clone https://github.com/displague/terraform-provider-linode.git
```

Enter the provider directory and build the provider

```sh
cd $GOPATH/src/github.com/terraform-providers/terraform-provider-linode
make build
```

Using the provider
----------------------

See the docs included in the website/docs directory:

- <https://github.com/displague/terraform-provider-linode/blob/master/website/docs/index.html.markdown>
- <https://github.com/displague/terraform-provider-linode/blob/master/website/docs/r/instance.html.md>
- <https://github.com/displague/terraform-provider-linode/blob/master/website/docs/r/domain.html.md>
- <https://github.com/displague/terraform-provider-linode/blob/master/website/docs/r/domain_record.html.md>
- <https://github.com/displague/terraform-provider-linode/blob/master/website/docs/r/nodebalancer.html.md>
- <https://github.com/displague/terraform-provider-linode/blob/master/website/docs/r/nodebalancer_config.html.md>
- <https://github.com/displague/terraform-provider-linode/blob/master/website/docs/r/nodebalancer_node.html.md>
- <https://github.com/displague/terraform-provider-linode/blob/master/website/docs/r/volume.html.md>

*The following links will not work until this repo is accepted by terraform-providers*

See the [Linode Provider documentation](https://www.terraform.io/docs/providers/linode/index.html) to get started using the Linode provider.

Additional documentation and examples are provided in the Linode Guide, [Using Terraform to Provision Linode Environments](https://linode.com/docs/platform/how-to-build-your-infrastructure-using-terraform-and-linode/).

Developing the Provider
---------------------------

If you wish to work on the provider, you'll first need [Go](http://www.golang.org) installed on your machine (version 1.8+ is *required*). You'll also need to correctly setup a [GOPATH](http://golang.org/doc/code.html#GOPATH), as well as adding `$GOPATH/bin` to your `$PATH`.

To compile the provider, run `make build`. This will build the provider and put the provider binary in the `$GOPATH/bin` directory.

```sh
$ make bin
...
$ $GOPATH/bin/terraform-provider-linode
...
```

In order to test the provider, you can simply run `make test`.

```sh
make test
```

In order to run the full suite of Acceptance tests, run `make testacc`.

*Note:* Acceptance tests create real resources, and often cost money to run.

```sh
make testacc
```

```sh
TESTARGS="-run TestAccLinodeVolume* -count=1"  make testacc
```
