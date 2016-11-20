# terraform-provider-dnspod

![Travis Status](https://travis-ci.org/3pjgames/terraform-provider-dnspod.svg?branch=master)

[Terraform](https://www.terraform.io/) [Provider Plugin](https://www.terraform.io/docs/plugins/provider.html) which manages DNS records in [DNSPod](https://www.dnspod.cn).

## Example

Config

```
provider "dnspod" {
  login_token = "${var.dnspod_login_token}"
}
```

Set an A Record

```
resource "dnspod_domain" "example_com" {
    domain = "example.com"
}

resource "dnspod_record" "www_example_com" {
    domain_id = "${dnspod_domain.example_com.id}"
    record_type "A"
    value: "127.0.0.1"
    ttl: 86400
}
```

## Import

To import domain, use the domain ID return from API. To import record, concat its domain id and record id with "-".
