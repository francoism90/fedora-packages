# fedora-packages

RPM specs for Fedora, built on COPR as `francoism90/fedora-packages`.

## Layout

- `packages/<name>/<name>.spec`: one directory per package, named after the package.
- `.copr/Makefile`: COPR `make_srpm` entry point. Takes `spec=` and `outdir=`.
- `.github/workflows/copr.yml`: on push to `main`, submits a COPR build for every package directory that changed. Needs the `COPR_CONFIG` secret.
- `.github/workflows/lint.yml`: rpmlint, SRPM build, actionlint, editorconfig-checker.

## Environment

The host is Fedora Atomic and has no `rpmbuild`, `rpmlint` or `copr-cli`. Run them in a toolbox:

```sh
toolbox create fedora-packages
toolbox run -c fedora-packages sudo dnf install -y rpm-build rpmlint rpmdevtools copr-cli make
```

## Rules

- Never commit source archives. `Source0` must be a downloadable URL; COPR fetches it.
- Build from the release tarball. No install scripts, no network in `%build` or `%install`.
- Bump `Release` on any spec change without a version change; reset it to `1` on a version bump.
- Add a `%changelog` entry for every change (`rpmdev-bumpspec` does this).
- Keep `rpmlint` free of errors.
- Commit subjects are short and imperative, like "Update kora-icon-theme to 2.0.7".
