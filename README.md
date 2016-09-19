## Ceph Rust
Rust-lang interface to Ceph. This library is under heavy development. Contributions welcomed.

This library is the core librados Rust interface that is used for larger Ceph related projects by LambdaStack.

### Ceph
Create a Ceph development environment or use an existing Ceph environment.

If creating a Ceph environment then use the following. It will generate a 4 node Virtual Box Ceph system with one
node being a bootstrap node that controls the other. The remaining 3 nodes are Ceph nodes (Mons, OSDs, RGWs, APIs).

Shameless plug - full disclosure: I created and manage github.com/ceph/ceph-chef (Chef cookbooks for Ceph) and the Bloomberg github.com link below for chef-bcs. Chef-bcs uses ceph-chef. These are the same tools we use at Bloomberg.

Requirements for Mac OSX:
1. VirtualBox
2. git
3. Locate an area where you would like to install the Ceph build environment
4. git clone https://github.com/bloomberg/chef-bcs.git

cd chef-bcs
cd /bootstrap/vms/vagrant
./CEPH_UP

This will take about 30 minutes to build out. It installs CentOS 7.2, downloads all of the parts required to get Ceph up and running with good options.

Once complete you can then login to the first node:
vagrant ssh ceph-vm1

Run ceph -s to make sure you see Ceph running. Now you can install the development environment and Rust.

### Rust
(In ceph-vm1 node)
curl -sSf https://static.rust-lang.org/rustup.sh | sh

### Yum
(In ceph-vm1 node)

mkdir -p projects/lambdastack
cd projects/lambdastack

Requirements for development:
sudo yum install -y git cmake
sudo yum install -y openssl openssl-devel

Clone ceph-rust project:
git clone https://github.com/lambdastackio/ceph-rust.git

NOTE: Make sure you have setup your favorite editor. Vim is automatically installed.

### AWS S3 Object Store for
Crate: aws-sdk-rust at https://github.com/lambdastackio/aws-sdk-rust and

------------
Portions originated from Chris Holcombe at https://github.com/cholcombe973