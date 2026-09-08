# Windows installation

Obtain the application only through the
[JE Horizon product website](https://pyre.jehorizon.com/). This documentation
repository does not host application files or GitHub release downloads.

The protected Windows package was tested with x86-64 CPython 3.10, 3.11, 3.12 and 3.13.
Python itself is a prerequisite. The installer checks the interpreter and
architecture before making a per-user installation; administrator access is not
part of the application installation.

The download includes the protected application wheels, base and GUI dependencies,
requirements, exact artifact hashes, an offline wheelhouse and third-party notices.
Follow the instructions supplied with the specific released package and compare
its SHA-256 with the value shown by the verified download flow.

Optional accelerator packages are separate from the base desktop installation.
Python package installation does not install GPU drivers or make unsupported
hardware compatible. Choose only a backend listed for the released application
and its documented interpreter and driver combination.

The desktop launcher uses the installed environment's `pythonw.exe`. This does
not transfer a signing identity to extension modules or guarantee that every
Windows security policy will accept a download. Do not disable normal protections
to install PyRe; report the exact warning and release version to support.

Purchased application use is offline and perpetual under its license. The planned
returning-download flow requires entitlement and email verification; that customer
journey is still being validated. No application download is hosted here.
