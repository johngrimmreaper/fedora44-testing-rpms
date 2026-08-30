# fedora44-testing-rpms

Public generated **testing Fedora 44 RPM repository**.

Paired private build-control repository: `johngrimmreaper/fedora44-testing-rpm-packaging`.

The `main` branch contains only repository documentation. Published RPMs,
SRPMs, signed `repodata/`, repository descriptors, the public signing key,
generated provenance and the static package browser are generated onto the
`gh-pages` deployment branch by `rpm-builder`.

Packages in this channel are testing/preview artifacts and are not the stable
Fedora 44 channel. Stable and testing publication are physically separated and
protected by the controller/destination pairing guard.

Legacy RPM binaries from `johngrimmreaper/rpm-packages` are intentionally not
copied into this repository.

Expected Pages URL after first publication:

`https://johngrimmreaper.github.io/fedora44-testing-rpms/`
