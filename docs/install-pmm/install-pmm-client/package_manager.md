# Install PMM client with Percona repositories

On Debian or Red Hat Linux, install `percona-release` and use a Linux package manager (`apt`/`dnf`) to install PMM Client.

!!! hint alert alert-success "Tip"
    If you have used `percona-release` before, disable and re-enable the repository:

    ```sh
    percona-release disable all
    percona-release enable original release
    ```

=== "Debian-based"

    1. Configure repositories.

        ```sh
        wget https://repo.percona.com/apt/percona-release_latest.generic_all.deb
        dpkg -i percona-release_latest.generic_all.deb
        ```

    2. Install the PMM Client package.

        !!! hint "Root permissions"
            ```sh
            apt update
            apt install -y pmm2-client
            ```

    3. Check.

        ```sh
        pmm-admin --version
        ```

    4. [Register the node](..//register-client-node/index.md).

=== "Red Hat-based"

    1. Configure repositories.

        ```sh
        yum install -y https://repo.percona.com/yum/percona-release-latest.noarch.rpm
        ```

    2. Install the PMM Client package.

        ```sh
        yum install -y pmm2-client
        ```

    3. Check.

        ```sh
        pmm-admin --version
        ```

    4. [Register the node](..//register-client-node/index.md).

## Package manager -- manual download

1. Visit the [Percona Monitoring and Management 2 download](https://www.percona.com/downloads/pmm2/) page.
2. Under *Version:*, select the one you want (usually the latest).
3. Under *Software:*, select the item matching your software platform.
4. Click to download the package file:

    - For Debian, Ubuntu: `.deb`
    - For Red Hat, CentOS, Oracle Linux: `.rpm`

(Alternatively, copy the link and use `wget` to download it.)

Here are the download page links for each supported platform.

- [Debian 9 (Stretch)](https://www.percona.com/downloads/pmm2/{{release}}/binary/debian/stretch/)
- [Debian 10 (Buster)](https://www.percona.com/downloads/pmm2/{{release}}/binary/debian/buster/)
- [Debian 11 (Bullseye)](https://www.percona.com/downloads/pmm2/{{release}}/binary/debian/bullseye/)
- [Red Hat/CentOS/Oracle 7](https://www.percona.com/downloads/pmm2/{{release}}/binary/redhat/7/)
- [Red Hat/CentOS/Oracle 8](https://www.percona.com/downloads/pmm2/{{release}}/binary/redhat/8/)
- [Ubuntu 18.04 (Bionic Beaver)](https://www.percona.com/downloads/pmm2/{{release}}/binary/debian/bionic/)
- [Ubuntu 20.04 (Focal Fossa)](https://www.percona.com/downloads/pmm2/{{release}}/binary/debian/focal/)
- [Ubuntu 22.04 (Jammy Jellyfish)](https://www.percona.com/downloads/pmm2/{{release}}/binary/debian/jammy/)

=== "Debian-based"

    ```sh
    dpkg -i *.deb
    ```

=== "Red Hat-based"

    ```sh
    dnf localinstall *.rpm
    ```
