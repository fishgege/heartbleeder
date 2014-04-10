# Heartbleeder

Tests your servers for OpenSSL
[CVE-2014-0160](https://www.openssl.org/news/secadv_20140407.txt) aka
[Heartbleed](http://heartbleed.com/).

**WARNING**: No guarantees are made about the accuracy of results, and you
should verify them independently by checking your OpenSSL build.

Pull requests welcome.

## Usage

```text
$ heartbleeder example.com
INSECURE - example.com:443 has the heartbeat extension enabled and is vulnerable
```

### Multiple hosts

Multiple hosts may be monitored by setting `-hostfile` flag to a file with
newline separated addresses. A web dashboard is available at
`http://localhost:5000` by default.

### Testing PostgreSQL

Postgres uses OpenSSL in a slightly different way. To test whether a Postgres
server is vulnerable, run the following (defaults to port 5432):

```text
$ heartbleeder -pg example.com
SECURE - example:5432 does not have the heartbeat extension enabled
```

### Installation

Binaries are available from
[gobuild.io](https://gobuild.io/download/github.com/titanous/heartbleeder).

Build from source by running `go get github.com/titanous/heartbleeder`, which
will put the code in `$GOPATH/src/github.com/titanous/heartbleeder` and a binary
at `$GOPATH/bin/heartbleeder`.

Requires Go version >= 1.2. On Ubuntu
[godeb](http://blog.labix.org/2013/06/15/in-flight-deb-packages-of-go) is an
easy way of getting the latest version of Go.

## Credits

The TLS implementation was borrowed from the Go standard library.
