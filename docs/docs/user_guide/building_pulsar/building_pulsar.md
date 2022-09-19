# Building Pulsar

If you want to investigate a bug, implement a new feature in Pulsar's core or just want to tinker then you will need to build and run Pulsar from source.

The main Pulsar application code can be found in the [pulsar-edit/pulsar](https://github.com/pulsar-edit/pulsar) repository.

## Requirements and dependencies

To build Pulsar you will need to meet some basic requirements:
- Node.js 16 (recommended installation is via [nvm](https://github.com/nvm-sh/nvm))
- yarn (enable with `corepack enable`)
- Git
- Python
- C++ toolchain
- [Libsecret](https://wiki.gnome.org/Projects/Libsecret) development headers

For OS or distribution specific instructions see below:

::::: details Linux
:::: code-group Linux
::: code-group-item Ubuntu/Debian

```
TODO: Ubuntu instructions
```
:::

::: code-group-item Fedora/RHEL

```sh
# Install development packages

dnf --assumeyes install make gcc gcc-c++ glibc-devel git-core libsecret-devel rpmdevtools libX11-devel libxkbfile-devel nss atk gdk-pixbuf2 gtk3 mesa-dri-drivers

# Install Node16 (using `nvm` - see above) and enable corepack (for `yarn`)

nvm install 16
corepack enable
```
:::

:::code-group-item Arch
```
TODO: Arch instructions
```
:::

::: code-group-item OpenSUSE

```sh
# Install development packages

zypper in -t pattern devel_basis
zypper in libX11-devel libxkbfile-devel libsecret-devel

# Install Node16 (using `nvm` - see above) and enable corepack (for `yarn`)

nvm install 16
corepack enable
```
:::
::::
:::::

::: details Windows
:::

::: details macOS
:::

## Building and running the application

To build the application so you can start hacking on the core you will need to download the source code to your local machine and `cd` to the pulsar directory:

```sh
git clone https://github.com/pulsar-edit/pulsar.git && cd pulsar
```

Make sure you are using the correct version of Node.js as described in the `requirements`

```sh
node -v
```

Run the following to initialize and update the submodules:

```sh
git submodule init && git submodule update
```

Now install and build Pulsar & PPM:

```sh
yarn install
yarn build
yarn build:apm
```

Start Pulsar!

```sh
yarn start
```

## Using ppm (Pulsar Package Manager)

`ppm` is used for installing and managing Pulsar's packages in much the same way that `apm` did on Atom. However at this point in the project there are a few hoops you have to jump through to get it to work correctly.

After following the build instructions you will find the `ppm` binary at `pulsar/ppm/bin/apm` but by default Pulsar will be looking in the wrong place for it. To solve this a couple of environmental variables need to be exported.

:::: code-group
:::code-group-item Linux
```sh
export ATOM_HOME=/home/<user>/.pulsar
export APM_PATH=/ppm/bin/apm
```
:::
:::code-group-item Windows
```
TODO
```
:::
:::code-group-item macOS
```
TODO
```
:::

You can now use the binary to link or install packages.

## Help and advice

If you have any issues then please feel free to ask for help in the Pulsar [Discord server](https://discord.gg/gp9UStzsHk), [subreddit](https://www.reddit.com/r/pulsaredit/) or [GitHub Discussions](https://github.com/pulsar-edit/pulsar/discussions).
If you think you have found a bug in the process then please create a [new issue](https://github.com/pulsar-edit/pulsar/issues).