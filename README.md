# Vauxite

## Usage

Clone this repo into the home directory:

```shell
git clone https://git.sr.ht/~hyperreal/vauxite.git
```

Ensure ostree and rpm-ostree are installed:

```shell
sudo dnf install -y ostree rpm-ostree
```

Run the `ostree-engine` script:

```shell
~/vauxite/ostree-engine --sourcebranch f39 --treefile vauxite.yaml --ostreebranch vauxite/f39/x86_64/main --destrepo /srv/repo
```

You can put the above command into a shell script to be run regularly by cron. I put mine in `/etc/cron.weekly`.

`/srv/repo` is assumed to be the document root of a web server.

### Rebase

```shell
sudo ostree remote add --no-gpg-verify vauxite <URL of your web server>
rpm-ostree rebase vauxite:vauxite/f39/x86_64/main
```
