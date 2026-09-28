# Third-party runtimes in the TaktSignal desktop distribution

The desktop installers bundle two runtimes so that nobody has to install them separately. Both are
redistributed unmodified; their exact versions and SHA-256 pins are in `desktop/build/runtimes.lock.json`, and
each payload records them in `build-info.json` and `payload-files.json`.

| Runtime                     | Version                   | License                                                                                                                                              | Source                                                                                                                                                                                                                                                                                                                                   |
| --------------------------- | ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Node.js                     | 22.22.2 (LTS line 22)     | MIT, plus the licenses of its bundled components (see `runtime/node/LICENSE` in the payload)                                                         | Official binaries from https://nodejs.org/dist/, verified against the published `SHASUMS256.txt`                                                                                                                                                                                                                                         |
| PostgreSQL (Linux, Windows) | 16.14                     | PostgreSQL License (permissive, BSD/MIT-like; see `runtime/postgres/COPYRIGHT` / `LICENSE`)                                                          | Relocatable builds by theseus-rs/postgresql-binaries (GitHub releases), verified against the pinned SHA-256                                                                                                                                                                                                                              |
| PostgreSQL (macOS)          | 16.15 (EDB build 16.15-4) | PostgreSQL License (`runtime/postgres/server_license.txt`) plus the component licenses in `runtime/postgres/commandlinetools_3rd_party_licenses.txt` | EnterpriseDB "PostgreSQL binaries" zip for macOS (`postgresql-16.15-4-osx-binaries.zip`, from EDB's download page https://www.enterprisedb.com/download-postgresql-binaries; EDB is the macOS installer provider listed on postgresql.org), verified against the pinned SHA-256; Developer ID-signed by EnterpriseDB (team `26QKX55P9K`) |

The PostgreSQL builds bundle OpenSSL 3 (Apache License 2.0), zlib (zlib License) and, on Windows, ICU (Unicode
License), libxml2 (MIT), libxslt (MIT), zstd (BSD), lz4 (BSD), libiconv / gettext (LGPL-2.1, dynamically linked
DLLs). On Linux the PostgreSQL binaries use the system's OpenSSL, libxml2, zstd, lz4, zlib and Kerberos libraries,
which the `.deb` package declares as dependencies.

**macOS (EDB build).** The EDB binaries bundle OpenSSL 3 (Apache License 2.0), ICU 68 (Unicode / ICU License),
libxml2 and libxslt (MIT), zstd and libedit (BSD), lz4 (BSD), zlib (zlib License), MIT Kerberos (MIT) and GNU libiconv
(LGPL-2.1, dynamically linked); the full texts are in `commandlinetools_3rd_party_licenses.txt`, shipped unchanged next
to the binaries. The build takes only what the server needs (`postgres`, `initdb`, `pg_ctl`, `pg_dump`, `pg_restore`,
`psql`, `pg_isready`, the libraries they load and the extension modules without external dependencies); pgAdmin,
Stack Builder, the language modules (PL/Perl, PL/Python, PL/Tcl) and the LLVM JIT are not shipped. The universal
(arm64 + x86_64) Mach-O files are **thinned** to the target architecture: the kept slice is byte-for-byte EDB's, so
EDB's per-slice code signature still verifies (`codesign --verify --strict` on the installed Mac: valid).

**LGPL-2.1 components — source code.** GNU libiconv (macOS, Windows) and GNU gettext (Windows) are shipped as
unmodified, dynamically linked shared libraries that users may replace with their own build. Their source code is
available from the GNU project: libiconv https://www.gnu.org/software/libiconv/ (archives
https://ftp.gnu.org/pub/gnu/libiconv/), gettext https://www.gnu.org/software/gettext/ (archives
https://ftp.gnu.org/pub/gnu/gettext/). The PostgreSQL builds that contain them come from EnterpriseDB (macOS) and
theseus-rs/postgresql-binaries (Linux, Windows). On request through the support route on taktsignal.cloud, the
TaktSignal project provides — or points to — the exact corresponding source for any library in a TaktSignal
download. The same pointer is published at taktsignal.cloud/docs/licenses and in every release's notes. This is a
licensing reading, not legal advice.

Headers, static libraries and PostgreSQL test / regression programs are removed from the payload; apart from the
macOS architecture thinning above, no file is modified.

The application's own npm dependencies (Next.js, React, pg, drizzle-orm, bcryptjs, zod and their dependencies) are
listed with their licenses in the SBOM (`sbom.cdx.json`) published with each release.

Development builds made with `--node-from-host` copy the Node.js binary of the build machine instead; they are
marked `runtimeProvenance: "local"` and must not be published (`npm run release:doctor` refuses them).
