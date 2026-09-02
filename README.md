# Reaper Fedora 44 Testing RPM Repository

Public, signed **testing RPM repository for Fedora Linux 44**, containing preview and pre-release packages maintained and published through the Reaper RPM build infrastructure.

# ⚠️ Stable repository required

Packages in this testing repository may depend on packages from the corresponding stable repository. Enable the stable repository together with this testing repository when the stable channel is populated.

Stable repository:

## **[https://johngrimmreaper.github.io/fedora44-rpms/](https://johngrimmreaper.github.io/fedora44-rpms/)**

# 🌐 Browse the testing repository

## **[https://johngrimmreaper.github.io/fedora44-testing-rpms/](https://johngrimmreaper.github.io/fedora44-testing-rpms/)**

The published site provides the complete package inventory, RPM metadata, repository descriptors, signing key, package browser, and current repository usage information.

## Configure the repositories

RPM package signatures and repository metadata signatures are enabled.

Repository signing-key fingerprint:

```text
E4C3 D7CD 3003 57A5 07C2 B237 FF30 3241 B8B8 606D
```

Install the signing key and testing repository descriptor. When the Fedora 44 stable channel is populated, enable its descriptor alongside testing, then refresh DNF metadata:

```bash
sudo rpm --import https://johngrimmreaper.github.io/fedora44-testing-rpms/RPM-GPG-KEY
sudo curl -fsSL https://johngrimmreaper.github.io/fedora44-testing-rpms/repo/reaper-fedora44-testing-fedora-44-testing.repo -o /etc/yum.repos.d/reaper-fedora44-testing-fedora-44-testing.repo
# When the stable channel is published:
# sudo curl -fsSL https://johngrimmreaper.github.io/fedora44-rpms/repo/reaper-fedora44-stable-fedora-44-stable.repo -o /etc/yum.repos.d/reaper-fedora44-stable-fedora-44-stable.repo
sudo dnf makecache --refresh
```

The testing repository descriptor enables `gpgcheck=1` for RPM package signatures and `repo_gpgcheck=1` for signed repository metadata. The stable descriptor uses the same signing policy when published.

## Repository architecture

The `main` branch contains repository documentation. Published RPMs, signed `repodata/`, repository descriptors, the public signing key, and the generated static package browser are deployed to the `gh-pages` branch by `rpm-builder`.

Paired private build-control repository: `johngrimmreaper/fedora44-testing-rpm-packaging`.

Stable and testing publication are physically separated. The testing channel may consume packages from the stable channel, while its generated deployment remains independently replaceable and rebuildable from the private controller.
