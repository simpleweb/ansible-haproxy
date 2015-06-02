# Ansible HAProxy Role for Debian Wheazy

This role achieves a good level of SSL security as tested by [SSLLabs](http://ssllabs.com/ssltest/).

In your playbook you need the following variables:

```yaml
app_name: my-app
ssl_certificate: <full SSL chain including key>
haproxy:
  backends: "{{ groups['production'] }}"
  backend_port: "8080"
```

### Limitations

This role only works with Debian Wheazy for time being.

SSL is forced for all connections.

haproxy.backends specifies a group in your hosts. This entire group becomes your front-ends and looks for resulting server on eth1 on port specified by backend_port. We use rackspace a lot and eth1 is the internal network.

### Results

It's worth checking results with SSL labs, but this should achieve A+ rating with good browser support.

![SSL Labs Result](https://tomsstuff.s3.amazonaws.com/aplus.png "SSL Labs Result")