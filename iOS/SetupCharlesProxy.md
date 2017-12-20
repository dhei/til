# How to Setup Charles Proxy on Mac

### Steps:
- In Proxy -> SSL Proxying Settings -> SSL Proxying, check Enable SSL Proxying box, add `*` to location.
- In Help -> SSL Proxying -> Install Charles Root Certificate, install root certificate on the Mac machine. Make sure to **always trust** Charles Proxy certificate in the Key Chain, otherwise you will get untrusted cert error.

---
Reference:
- [Charles Proxy's documentation](https://www.charlesproxy.com/documentation/proxying/ssl-proxying/)
