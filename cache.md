# Debian/Ubuntu apt cache

/etc/apt/apt.conf.d/00aptproxy

    Acquire::http::Proxy "http://<ip>:3142";
    Acquire::https::Proxy "false";

