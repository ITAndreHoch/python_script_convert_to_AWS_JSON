# python_script_convert_to_AWS_JSON
Python script - conversion json for file to AWS compliance JSON standard

# Project goal:

Automatic conversion files imported from other supplier and convert it into AWS Route R53 JSON standard:

# Example file before conversion:

```
{
        "a": [
            {
                "active": true,
                "name": "blog",
                "target": "10.10.10.3",
                "ttl": 14400
            },
            {
                "active": true,
                "name": "",
                "target": "10.10.10.4",
                "ttl": 600
            },
            {
                "active": true,
                "name": "ski",
                "target": "10.10.10.5",
                "ttl": 14400
            }
        ],
        "aaaa": [],
        "afsdb": [],
        "cname": [
            {
                "active": true,
                "name": "_12341234567890.www",
                "target": 3334445555.com.",
                "ttl": 14400
            },
            {
                "active": true,
                "name": "lp",
                "target": "page.com.",
                "ttl": 14400
            },
            {
                "active": true,
                "name": "_12324556678",
                "target": "2233445566.com.",
                "ttl": 14400
            },
            {
                "active": true,
                "name": "www",
                "target": "www.my_domain.be.edgekey.net.",
                "ttl": 300
            }
        ],
        "dnskey": [],
        "ds": [],
        "hinfo": [],
        "id": 384515,
        "instance": "andre@my_domain.com",
        "loc": [],
        "mx": [
            {
                "active": true,
                "name": "",
                "priority": 10,
                "target": "mailin01-domain.pwd.io.",
                "ttl": 14400
            },
            {
                "active": true,
                "name": "",
                "priority": 40,
                "target": "mailin04-domain.pwd.io.",
                "ttl": 14400
            },
            {
                "active": true,
                "name": "",
                "priority": 30,
                "target": "mailin03-domain.pwd.io.",
                "ttl": 14400
            },
            {
                "active": true,
                "name": "",
                "priority": 20,
                "target": "mailin02-domain.pwd.io.",
                "ttl": 14400
            }
        ],
        "name": "my_domain.be",
        "naptr": [],
        "ns": [
            {
                "active": true,
                "name": "",
                "target": "a1-1345.tptp.net.",
                "ttl": 172800
            },
            {
                "active": true,
                "name": "",
                "target": "a9-12.tptp.net.",
                "ttl": 172800
            },
            {
                "active": true,
                "name": "",
                "target": "a13-44.tptp.net.",
                "ttl": 172800
            },
            {
                "active": true,
                "name": "",
                "target": "a2-3.tptp.net.",
                "ttl": 172800
            },
            {
                "active": true,
                "name": "",
                "target": "a22.tptp.net.",
                "ttl": 172800
            },
            {
                "active": true,
                "name": "",
                "target": "a1.tptp.net.",
                "ttl": 172800
            }
        ],
        "nsec3": [],
        "nsec3param": [],
        "ptr": [],
        "publisher": "https://control.something.com",
        "rp": [],
        "rrsig": [],
        "soa": {
            "contact": "hostmaster.something.net.",
            "expire": 604800,
            "minimum": 14400,
            "originserver": "something.net.",
            "refresh": 28800,
            "retry": 7200,
            "serial": 201803333303,
            "ttl": 14400
        },
        "spf": [],
        "srv": [],
        "sshfp": [],
        "time": 1547736949,
        "txt": [
            {
                "active": true,
                "name": "",
                "target": "3j33rjd",
                "ttl": 300
            }
        ],
        "version": 1.0
}
```
