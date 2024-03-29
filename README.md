ansible-role-vault
==================
[![Molecule](https://github.com/austincloudguru/ansible-role-vault/workflows/Molecule/badge.svg?event=push)](https://github.com/austincloudguru/ansible-role-vault/actions?query=workflow%3AMolecule)
![Latest Version](https://img.shields.io/github/v/tag/austincloudguru/ansible-role-vault?sort=semver&label=Latest%20Version)
[![License](https://img.shields.io/github/license/austincloudguru/ansible-role-vault)](https://github.com/austincloudguru/ansible-role-vault/blob/master/LICENSE)


This role installs vault server in AWS.

Requirements
------------
This role is written to run in AWS using the AWS provider for the retry_join configuration parameter using the `role: consul` tag.

    "retry_join": ["provider=aws tag_key=role tag_value=consul"]

If you want to run it outside of AWS, you will need to update the retry_join value in the consul role to use a different method.


Role Variables
--------------

### Default
For most people, the default variables that are set should be fine, but there are use cases for changing them. They are:

    vault_group:       # Default group name (vault)
    vault_gid:         # Default gid (10010)
    vault_user:        # Default username (vault)
    vault_uid:         # Default uid (10010)
    vault_version:     # Default vault version (0.10.4)
    vault_consul:      # Default consul location (127.0.0.1:8500")
    vault_consul_path: # Default consul path (vault)
    vault_address:     # Default vault address (0.0.0.0)
    vault_port:        # Default vault port (8200)
    vault_start:       # Start Service by Default (True)


### Playbook Variables
Within your playbook, you should set the following variables:

    vault_cert:          # SSL Certificate for the cluster
    vault_key:           # SSL Key for the cluster

Dependencies
------------

This role is designed to be used with my [vault role](https://galaxy.ansible.com/AustinCloudGuru/vault) on Ansible Galaxy.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables
passed in as parameters) is always nice for users too:

    - name: Converge
      hosts: all
      vars:
        consul_role: client
        consul_datacenter: "us-east-1"
        consul_encryptkey: "YKbtX0Gc3mnJ7QwaNwNYtg=="
        consul_cert: |
          -----BEGIN CERTIFICATE-----
          MIID0DCCArigAwIBAgIBCjANBgkqhkiG9w0BAQUFADBkMQswCQYDVQQGEwJVUzEO
          MAwGA1UECAwFVGV4YXMxDzANBgNVBAcMBkF1c3RpbjEbMBkGA1UECgwSTWFjbWls
          bGFuIExlYXJuaW5nMRcwFQYDVQQLDA5Db25zdWwgQ0EgQ2VydDAeFw0xNzEwMDUw
          MjE3MjZaFw0xODEwMDUwMjE3MjZaMGkxHzAdBgNVBAMMFmNvbnN1bC5tYWNtaWxs
          YW4uY2xvdWQxDjAMBgNVBAgMBVRleGFzMQswCQYDVQQGEwJVUzEbMBkGA1UECgwS
          TWFjbWlsbGFuIExlYXJuaW5nMQwwCgYDVQQLDANTUkUwggEiMA0GCSqGSIb3DQEB
          AQUAA4IBDwAwggEKAoIBAQDHa1FiN4520HHaCO7PyMy+DTJYciDxF7zdtLzujSkB
          BKMF2xKyKRZE8QbQjP5zgvOzkGxpFlTaMudAYrNEGJTZctlBqOZxVOi1zwHUKWfG
          rImcBYiY+W22DgD+IXF6qyD88peXjzggyMBt+7wuqrto/Y7A+PrNN1ZICNlaCeh9
          MGJgnS3Vjc7oMfZMix+Q/nmu12Nunqd/qS0mXBvWFb3WQehG5az3t/Z1QTTh6eYv
          1TabdV5QKRbZuOLIn3l9Di29b/7xOCZzhjqIr9X2ERuB97XOXCFoG3NaT0l2uWf/
          TzHFxqQe+hZVV2YpjSUPtRv62cIKX1JylI9wIPN6jwJZAgMBAAGjgYcwgYQwCQYD
          VR0TBAIwADAdBgNVHQ4EFgQUJYbDAwcNvH+YYWcqoNg26nezGGUwCwYDVR0PBAQD
          AgWgMB0GA1UdJQQWMBQGCCsGAQUFBwMBBggrBgEFBQcDAjAsBgNVHR8EJTAjMCGg
          H6AdhhtodHRwOi8vcGF0aC50by5jcmwvZGVtby5jcmwwDQYJKoZIhvcNAQEFBQAD
          ggEBACBvIpqeepCaWwiWy+5yPLMUOyC+VqiXgok6kLdX1CiiUkGF5KLWXU1GuWEq
          18oW5AdMvYuxOf4yYQYOIHYdYl6jCGdekHXTD1BDuWc8hvCucfQjLBsWJVwkjEEV
          +mZyi6dxnmxaGkhKlC8T35XeJeJfacARBMHgFS/UWCDKzFc+Wkbos1ZyiaHoxhHW
          TowkYnFqhErc4msOYYSRGhM3ryC05CPwVRymagTzmRoxnb6yqRh240CzYRyr3gex
          jgTb7gAnrK95CKUZqCA33Ff3EsqvNUPX5DneplhRdqb9ehAFcYgq1tU/E957Bkme
          rkt6x7V4L2FK+ukkxgSPE/RpbGc=
          -----END CERTIFICATE-----
        consul_key: |
          -----BEGIN PRIVATE KEY-----
          MIIEvgIBADANBgkqhkiG9w0BAQEFAASCBKgwggSkAgEAAoIBAQDHa1FiN4520HHa
          CO7PyMy+DTJYciDxF7zdtLzujSkBBKMF2xKyKRZE8QbQjP5zgvOzkGxpFlTaMudA
          YrNEGJTZctlBqOZxVOi1zwHUKWfGrImcBYiY+W22DgD+IXF6qyD88peXjzggyMBt
          +7wuqrto/Y7A+PrNN1ZICNlaCeh9MGJgnS3Vjc7oMfZMix+Q/nmu12Nunqd/qS0m
          XBvWFb3WQehG5az3t/Z1QTTh6eYv1TabdV5QKRbZuOLIn3l9Di29b/7xOCZzhjqI
          r9X2ERuB97XOXCFoG3NaT0l2uWf/TzHFxqQe+hZVV2YpjSUPtRv62cIKX1JylI9w
          IPN6jwJZAgMBAAECggEBALd39dUd9fU8CzMk+smyHSRRMduLjOEjDMEREq2Ks4nb
          QT0W85l0Eaf19GYVAdk2Ro4StprsT768DGQBKprg3rk8X8N36COmkb8LJ8yRF4gC
          n0wrDyRmfth7A9DK5gOMw/nUG0H2IxaOe/P0IYrxyyBp/1ds+hmp6ri1Y3riGMJr
          DGc18YPR7ViY7zkLS0gYDe90QI0vAG8ZfTsOmPYFJk0DSe4Tl+19udpGvXSFxfg2
          QtkfYnCMAAxgcwlOCbuZ2u4WLCvTG+ChmEJsT/NnHgjAZXxiG4hcJcuk3S2Jcj+f
          0XTGCpgDUneh112hIh2qq4BQdzQ/68/QEx7cYBDaQj0CgYEA6eW5L9BxDyunyuLm
          EVksDFWZTTg3CqV7OCDy6pCKp50zgFfX+u9H7o4MqU3D9DoEg2aZA6gCXVc9/QYw
          Jhcc7nrZLjWIPXiSmCl2vLOkAG/bF1euejhhLGmtg6ED3apcgaFqBaHsyO123uJY
          VV2sgAGMTCuuBTRWF/Ab+uS58bMCgYEA2kOGJPr4sn7x4Me99cCNUXohL4Yp8KE6
          D3qE4RMTzd6hkuh8vn1gbiz+vDaPv4mJv5O8eW49tXY7q/ITmpFU9Q+XrRkmCJQc
          xJjjD3Pxz3MTSjyL80k4ghFXy30N6twOqt/vO7OQZLT1Rfv/m76qb9juzF3KMc3A
          kzrH/Bu6/cMCgYEAuhdp5V7j9Pv4vfUUswzNfOrF06g8Mp5CkP+2BWYGyyDJjv1U
          +3NROb2O2Uzj8PYQDTOd3kjXyMfWq+82c7fD7wGSta8lvDKn/6RNsgkDHM3h9Ipw
          aRFeTuWthaKf3sbiXsi7/8s7BwnXn7FaMmEbE6UnqJrAE6f2L4l72XwNbP0CgYAm
          y7PPZPDJwXi67KYeRZCY9+1oJh/UTsQkNjHiU+LESBtOIpbxwRVf4A2TZNteP1NF
          wzvQFcFQPOjUYl4LrmN8f74FHaA+DB2k8EwD1icYKas3GdYCc3Rg4jZJzDuqEF1n
          EBDU+tDipaunOeiwRU7EPLoNh2pGOf1N7jfX3xH4wwKBgCkt/CO9mr8aC5X+8hAs
          j7lBwtsV67nbB6DhRlVMwwLj75EGf2qDVfDl7fGkjudhf9fN5YxlBU2lUACp+GPC
          VhfycE+bg0JxDMvMEhI2y8SQ44RZZ49i8QJQWL1adTQi/smi3tF85g+tH4aXsJfE
          ZazHZyqVNJx0P4AAkdhIJznE
          -----END PRIVATE KEY-----
        ca_cert: |
          -----BEGIN CERTIFICATE-----
          MIIDRDCCAiwCCQDEav6U/66tTzANBgkqhkiG9w0BAQsFADBkMQswCQYDVQQGEwJV
          UzEOMAwGA1UECAwFVGV4YXMxDzANBgNVBAcMBkF1c3RpbjEbMBkGA1UECgwSTWFj
          bWlsbGFuIExlYXJuaW5nMRcwFQYDVQQLDA5Db25zdWwgQ0EgQ2VydDAeFw0xNzEw
          MDUwMjE0NDNaFw0yNzEwMDMwMjE0NDNaMGQxCzAJBgNVBAYTAlVTMQ4wDAYDVQQI
          DAVUZXhhczEPMA0GA1UEBwwGQXVzdGluMRswGQYDVQQKDBJNYWNtaWxsYW4gTGVh
          cm5pbmcxFzAVBgNVBAsMDkNvbnN1bCBDQSBDZXJ0MIIBIjANBgkqhkiG9w0BAQEF
          AAOCAQ8AMIIBCgKCAQEAwWEC0XIjruB/Vv2w7VLaGGlcX04DrmBV+lZpG6IigAdi
          QfuA00RtsjVxi4VCYARR66W2bKrTrKFpuRrOCt+OzcCu1T0Z0+VfxDiJmCfNfUxt
          IFG3+42DJmGhfLWFp06fBxEWzvwDFbbND3F8mAJXSMIs5HrPnSFIdWR5eC2t/vBb
          T4IB1ntt4QulE+sKrxxfeDDeoeVuj5LG9pmM4VrAnaRbcfp4UDGAbv9W0TbSsqWc
          oe0bp/5+d1i7Z/fes20k1kzjI7N3M3RUPf7hI3TV24ljGxHCGaqR/3Ozv0bhmm28
          Mr1ScEwBY1BsDkuvGwZlkmU4sjZGrYQwv8DFHExAIQIDAQABMA0GCSqGSIb3DQEB
          CwUAA4IBAQB4wyRZSwvs9qgHUb8fl83pSQAnFNg3qffqNN2wBQbNUcCFUtx/XL6d
          J0i/AEvBmy9SXnTTSuN4udDkdxpznWtHtagIvC7CA70zRxF0PPdhOCBqInrAX0l3
          vFSBXIONfI1wMxdUCkP/A3EZEAIsON0zhVpUhbwaNkiEeuMahG3VFv2VFt/ANE1L
          QCulz7aUoUEXfXjDmpidVD/wzqBjUbJc0FEqTniaBDBNaN7bEogNZlRU/vGhZ2O1
          KBn9wSWwYRXmLICv7s6GrsYMoOFit4FrXQdj42hzqpGugXbAlOTknV6KZbwptSuG
          lEhOBOqUfdiXqUszPbSsRtFpmA+hA0vT
          -----END CERTIFICATE-----
        vault_cert: |
          -----BEGIN CERTIFICATE-----
          MIIGATCCA+mgAwIBAgICEAEwDQYJKoZIhvcNAQELBQAwgZoxCzAJBgNVBAYTAlVT
          MQ4wDAYDVQQIDAVUZXhhczEbMBkGA1UECgwSTWFjbWlsbGFuIExlYXJuaW5nMTEw
          LwYDVQQLDChNYWNtaWxsYW4gTGVhcm5pbmcgQ2VydGlmaWNhdGUgQXV0aG9yaXR5
          MSswKQYDVQQDDCJNYWNtaWxsYW4gTGVhcm5pbmcgSW50ZXJtZWRpYXRlIENBMB4X
          DTE3MTAwNDIyMjg0NFoXDTE5MTAwNDIyMjg0NFoweTELMAkGA1UEBhMCVVMxDjAM
          BgNVBAgMBVRleGFzMQ8wDQYDVQQHDAZBdXN0aW4xGzAZBgNVBAoMEk1hY21pbGxh
          biBMZWFybmluZzEMMAoGA1UECwwDU1JFMR4wHAYDVQQDDBV2YXVsdC5tYWNtaWxs
          YW4uY2xvdWQwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQCz4uAZlC/W
          I+bufofEY+5GBA8SQX95xRxC2JDJmobcCLMp1kNSEYL0lKEbEKTa6fre9jmdo3p4
          3yGT2IH5gZymTWTCdXJPGGCv91wjt/dtXewmXCf/QpoGfxkFvlZsJ0i6FL3VZDfQ
          nWfnhKY3udU+pFJaIkwZ1j3QwpBpCDK9I7oBoNP60UsL89fkHgJTwqEbcOU9syZF
          uNUF8SMgCMtrUoPa80XZ2vazDILPxPDPaKQmtrA3kGyeRttAylDearJL/wvYIX+G
          9ZdRUVJ7/8ZakyWvW19skKghFEcmHf0+nDygU7ofgG5Dqnav8Nl3QjDcSTZE1Zvt
          NCbz3GGi4WxpAgMBAAGjggFvMIIBazAJBgNVHRMEAjAAMBEGCWCGSAGG+EIBAQQE
          AwIGQDAzBglghkgBhvhCAQ0EJhYkT3BlblNTTCBHZW5lcmF0ZWQgU2VydmVyIENl
          cnRpZmljYXRlMB0GA1UdDgQWBBSv+87V9sra2nH5NgMZyH78BN5mQjCB0QYDVR0j
          BIHJMIHGgBRr0Ny9XNuCDz6qJMyoFMN6tU3XrKGBqaSBpjCBozELMAkGA1UEBhMC
          VVMxDjAMBgNVBAgMBVRleGFzMQ8wDQYDVQQHDAZBdXN0aW4xGzAZBgNVBAoMEk1h
          Y21pbGxhbiBMZWFybmluZzExMC8GA1UECwwoTWFjbWlsbGFuIExlYXJuaW5nIENl
          cnRpZmljYXRlIEF1dGhvcml0eTEjMCEGA1UEAwwaTWFjbWlsbGFuIExlYXJuaW5n
          IFJvb3QgQ0GCAhAAMA4GA1UdDwEB/wQEAwIFoDATBgNVHSUEDDAKBggrBgEFBQcD
          ATANBgkqhkiG9w0BAQsFAAOCAgEAh2h3phGaEWTBtzSzoHZnSNx3/XPK9tpQhVuC
          xIoMr0uhojlbQvEBFQwsNDW+YhmFlnxRZMC8knVM25qGxB/NWnGo1OEZsc+dNn1M
          PYfQL68nsHZssEg//QKxwdb9fP8oS1Nnood6dX0hQnB7djMaP/Sq0goLt0aFyttt
          GLocdADKS8IySxLSvv8zWksBc5tk+LxmfuQV74vk3+ldLe+ehcNFnjoR5r1IZxWy
          t38ezaUcWilejknUehbl/Xh06WVucEDWdx4xsrWL845eDMzify6wEa/fnBQDYXO8
          68uGXQ3wmWZ+hNc81So9MMVv2TsuwfTXPXAfrHDi2liq6ybmrwFbuMY5+gUPlXHY
          Yly0O3tYFugIlaFwSsrplehOcQSLOCQA7Xp6Fvek4TAGFdiTc+8YlFmKG9XYR4uq
          axI7L/yaurA+VB1wj5ElDcRQa4HIJwVycmoh2WtPagF1fmyYltIdgWheWn8FZzQN
          RgRou5A2KGbqNlvDFpvkUYWD7aSocWgL7XLzyurBUwvYtoWOKgeWOMzv/0J4oT+v
          0biTsGXWF+2jIh7Max90rINSG7nPGOl5LuDpexpAKI0dtRzimYtE7tidzaZnkLRH
          te2nKouwG0Y4UEdGLOkLHEVpdILsV4U5z9nuhK9AHUCsiZpr16JRvMUQWnOwYOcP
          8i3G9eI=
          -----END CERTIFICATE-----
          -----BEGIN CERTIFICATE-----
          MIIGITCCBAmgAwIBAgICEAAwDQYJKoZIhvcNAQELBQAwgaMxCzAJBgNVBAYTAlVT
          MQ4wDAYDVQQIDAVUZXhhczEPMA0GA1UEBwwGQXVzdGluMRswGQYDVQQKDBJNYWNt
          aWxsYW4gTGVhcm5pbmcxMTAvBgNVBAsMKE1hY21pbGxhbiBMZWFybmluZyBDZXJ0
          aWZpY2F0ZSBBdXRob3JpdHkxIzAhBgNVBAMMGk1hY21pbGxhbiBMZWFybmluZyBS
          b290IENBMB4XDTE3MTAwNDIyMTUzMFoXDTI3MTAwMjIyMTUzMFowgZoxCzAJBgNV
          BAYTAlVTMQ4wDAYDVQQIDAVUZXhhczEbMBkGA1UECgwSTWFjbWlsbGFuIExlYXJu
          aW5nMTEwLwYDVQQLDChNYWNtaWxsYW4gTGVhcm5pbmcgQ2VydGlmaWNhdGUgQXV0
          aG9yaXR5MSswKQYDVQQDDCJNYWNtaWxsYW4gTGVhcm5pbmcgSW50ZXJtZWRpYXRl
          IENBMIICIjANBgkqhkiG9w0BAQEFAAOCAg8AMIICCgKCAgEA0fAZ5dlWFyAZg0XU
          5lEXDZ5AuRY9Owd2Wu64ZbhX4fhfQdcGyNjAeS7CLYaKmK1vIJCD1E+dAj8Acv0Y
          0vzxsXg2ZMHZJ0HACviHlvuFWypr+USdBsoqxmwNNIVo7Iz4deurDTqMTTpu93ct
          +1/DKTZJGJ/9KNZabof09gKHQsXAKOpufkkOvfr23Nrs3aTI6//O7h7PBh7bLaRw
          3Zv8YreSR4d559IYTjvXEgdXoGNOvtHv4PFVqRHuapuT05Cj9VNZ6xECsN/8heku
          hSvSeqdkNZO1N2fg4w33tLuolnj5ZprUdnhtlEUNngqMUc/EPGyoM5WSLqCE7Pou
          +Ce0qtGdk5nMboUDqeoZMMDxIpJkNwXzkiEty5IMo4+dbSbX4Ow4SdvlwlE1vIzl
          Qkff731bvIX6ZtceQKBULDVna54+zrO0avVmUwPVcaJdLfXeslJH1N/BFd00b9kB
          2m5dlunk7AXdccC9FVChCjtKvIs7vzUqHZ0B42pkxPEfcFX+jOJ6/jEDOJAECy/C
          uR5A7MluDIOnfmL+NWwbJUzSjQ4hB3tqglD+cfBb60xZmpYaT8TkqYZhqNwNfZs0
          vqUGBXF6baWnbE4ifABYiAq/dTW7hapaF46JnukplNVkBtvtk6LF+jAqvgmomNpf
          b8HT4jof9N5G/vUR6MdxK/9JpeMCAwEAAaNmMGQwHQYDVR0OBBYEFGvQ3L1c24IP
          PqokzKgUw3q1TdesMB8GA1UdIwQYMBaAFBsFIWXvq4NkjbiyD5FbDZsxdgcKMBIG
          A1UdEwEB/wQIMAYBAf8CAQAwDgYDVR0PAQH/BAQDAgGGMA0GCSqGSIb3DQEBCwUA
          A4ICAQBQpiMnuhHBQ0ovi4hRIZ9E2gI7eAk2v/af8UfK7SlmWzJRu5VkwLIJVDlc
          vPzTFmp0wErJroNHSa//QGw6lxq2eFOMOVtgtHZMKa4Ck6arC8ucyGv2/pNWqreU
          GQVSwYbs1aU+tyBYcSm/Kwf5iZKJsCYjaVouUyCfamWcqsDW9ml7xOay8zHxEuyl
          I7NU7eDTx99Upa09nxE9SxmnYFCtfJO7Oah18CaJildFMu//eFGjDA2FeDWxUHTd
          4xrvvia4nxVooRI/r0unlvpiaUQ08oMYlv5S8TPwf9AsEQw6IGecPeN9+iEJO5BO
          p1l0ILzv6YKKn60pah4kqgHX0XVX/aSxQms6Rjaj0A/lw0q8b0z/qHLAzHdo/ozu
          VLZ7J6R2RRI5ojwrdDWro02wvAFjyScyoF+aqyWPWcHW63ITq4jgYxGCHKQzoZzn
          R7KwSJI7ri+PShVOs+BkqDdq7nAqWtAxhjBEvqKTQ08Z5WQiBLPQLABGxQ0K53+Q
          9xQpiJMDSmQQrsIpXMkMbQ0SWAyHC0SqLgZmanq2SeOXbfDJ9VV+CcCj8QdYJn2p
          1SUD8rv4sDOl1cnNXkZU3K0TkyZzuvMLgfw9NsPeAGOLMbb1thdaeNv7oQB/Xfce
          K5I6KkIhqmZFltXlOlCS1RFD3foI2+uhhvpY1NlLnb+Ala0ODw==
          -----END CERTIFICATE-----
          -----BEGIN CERTIFICATE-----
          MIIGLjCCBBagAwIBAgIJAOiF4nw94NCqMA0GCSqGSIb3DQEBCwUAMIGjMQswCQYD
          VQQGEwJVUzEOMAwGA1UECAwFVGV4YXMxDzANBgNVBAcMBkF1c3RpbjEbMBkGA1UE
          CgwSTWFjbWlsbGFuIExlYXJuaW5nMTEwLwYDVQQLDChNYWNtaWxsYW4gTGVhcm5p
          bmcgQ2VydGlmaWNhdGUgQXV0aG9yaXR5MSMwIQYDVQQDDBpNYWNtaWxsYW4gTGVh
          cm5pbmcgUm9vdCBDQTAeFw0xNzEwMDQyMjA5MzhaFw0zNzA5MjkyMjA5MzhaMIGj
          MQswCQYDVQQGEwJVUzEOMAwGA1UECAwFVGV4YXMxDzANBgNVBAcMBkF1c3RpbjEb
          MBkGA1UECgwSTWFjbWlsbGFuIExlYXJuaW5nMTEwLwYDVQQLDChNYWNtaWxsYW4g
          TGVhcm5pbmcgQ2VydGlmaWNhdGUgQXV0aG9yaXR5MSMwIQYDVQQDDBpNYWNtaWxs
          YW4gTGVhcm5pbmcgUm9vdCBDQTCCAiIwDQYJKoZIhvcNAQEBBQADggIPADCCAgoC
          ggIBALLsahNFlSWZN56lNZMYqY2c9rBUtrUWc2OIAuWj776iGjULhrabfVD7/hhC
          6VmHyxQI0BxsU+eaz0m4LOPiDcZPrmktnJ9sQGIPHGgsPVtYRpMhXo/qfyv3fNWf
          8+d86wS6np3JxUKmyfQlUNMvGC3H/ivmq+bgImdu43atjaBgAoYI02rnVyNZGDMM
          y3nyovy5F+SE93bh+TJDLGu/0+o3d1rXAcDAcAxqXqwgbQT1cMzQ8Ls/BefLL/R+
          Sf9YFmWOAaPK77pwcTL8bShsLLGlcbi3plPzT/tcXPhzUDlsyZWL1oZGUQLxJA4p
          Xb5c+7MkEqa66j5Z6hYAl8HH1CJYbvon6DDDvAh5uZsWTk09kUqwbK8FeBOse1pf
          sU+YtX2k7GWpeuR6Q7nayphFKVI0mJcr6o7t/CS3hXJS2pQ3h2rO30OT0xm8isC1
          Gc8xTAzUCTwho9IIcuoezYlbps+tnS7BI+kxh8xTGGadgKaru6CwcwuhFkBj0oQQ
          ds7wu/VTIizTjUHBaQTztu4ZTYV95Dse0LuXM+7YxM/3AEVbJ8LB0brOOJfiZTQh
          7phik+e6bKprAR7XVkiHXcUwb4BOXxx8z66ryJpUvT4X1WYAuOnOEIbk/iymGPtc
          IVkuEIPV7kxe9sizqyRcSJxl+RCiCZqCQLGrrUK4TyRpkksLAgMBAAGjYzBhMB0G
          A1UdDgQWBBQbBSFl76uDZI24sg+RWw2bMXYHCjAfBgNVHSMEGDAWgBQbBSFl76uD
          ZI24sg+RWw2bMXYHCjAPBgNVHRMBAf8EBTADAQH/MA4GA1UdDwEB/wQEAwIBhjAN
          BgkqhkiG9w0BAQsFAAOCAgEAqI4SOgoOmQj2S1vGaN/JHsuBuz+rDaopZkdFOUsm
          iWEUjzTxBNPRAc9C+jeyjd+PpZVvvJU1FPRXdcxcsZ617f8cN9JSWPV6GhNWn7+x
          bV1VJd8I5eBUV22F6wcRPzR31Kgyx80JYF3S/9c/wLnJS9zF8dR2ZXGbJGZI0Clk
          0oZ1HRJqWmG/W3UHxM5BZd9M0m2dm0G0vcP2DADAcgITUYn0DXdYm4zsgzuCUX/I
          P5I9V3xJUvcFCl0VfQh+2mYcpoySIhcJWVdJmUg2mpQVMuvWXNvtszmutcQayX+L
          KgQDPpEwFadJ9ycOJsdbrbHd6STWYTEZORHUkQWulunIat+WiKNP3JyyzLPrODFs
          Pq1STk/dr+xUSXdxq+DHI3DGoQGaOVPaRatgUqZqHVa8hyqcVcNsQx6gNtCe8w1H
          bIoOSW7vrdf/a0LLm+E9g6T81cSmoghEmkexhLBrDfvmF8+SWE11mWBaJSzrLfrs
          r/EjkBZW3I0zuWYffq0jpKJsfh9aWX4It5BNbUf04WJzqJtrYSmuRKR6TDqrZMyd
          hte0EwVv3Yx4n51b9GHspAptBLOBYOPNFjxSuitT/9e3UU9rokHi24WPNmrabNbI
          aGmHR4XrwXzkYMq7sc8/oXZFMM5lf5az0muFTp3q0YKDamB8B5CkAKpxj2UdbCoD
          RNU=
          -----END CERTIFICATE-----
        vault_key: |
          -----BEGIN RSA PRIVATE KEY-----
          MIIEpQIBAAKCAQEAs+LgGZQv1iPm7n6HxGPuRgQPEkF/ecUcQtiQyZqG3AizKdZD
          UhGC9JShGxCk2un63vY5naN6eN8hk9iB+YGcpk1kwnVyTxhgr/dcI7f3bV3sJlwn
          /0KaBn8ZBb5WbCdIuhS91WQ30J1n54SmN7nVPqRSWiJMGdY90MKQaQgyvSO6AaDT
          +tFLC/PX5B4CU8KhG3DlPbMmRbjVBfEjIAjLa1KD2vNF2dr2swyCz8Twz2ikJraw
          N5BsnkbbQMpQ3mqyS/8L2CF/hvWXUVFSe//GWpMlr1tfbJCoIRRHJh39Ppw8oFO6
          H4BuQ6p2r/DZd0Iw3Ek2RNWb7TQm89xhouFsaQIDAQABAoIBAQCg5+nJN5JqnAav
          gqLy+uhh3LOWgtwCElyrNoicrQrAu093tt7VBDD9kg1h5ktwPidXVSxIY7jjccPZ
          OatZgaSb5VKh1uh+87FY9YyHrsE2JPNdhMWKQQsBkKLTTmSDrcgSGweLX2/FvWb5
          4t/DrQigVeAMG+2ylr8Ig2Elcl3gbBkdRuQg+kWh2X6P2oBeio/SHV6WcwNena5K
          O4/23bf1i+TkKHDz7jvoyg+fyhjkoni1aV+pvuu5EcMBJvoku+b7bSwsxnSrwr0o
          SUaMNwDFrvwOqQ9UBWdaL7HhuVi27Agl/gRaVBDAvP2z2RyecVNESgTpzgCCKYBw
          EZpFAL8BAoGBAOuEXznLsiadaHYuGWIblfKm/e5z8OFefKLkgiPgPaR83cg2eCLg
          kcczY4NBmCWg/o0ip4NIIOmD3o76u5KttCtHi9s1wg+Zx42LGZTCw4NkOP1AC3rc
          nuhKsnz9Dul7UEdGwh4ZjTBAcwbrkzStbU1Nq9pJgErTyHSVtNxyNef5AoGBAMOH
          65xVS75pC8BGqiZyT+vXuO2rss1a3iClSk4UZ6JYUgx1DwgxpkFCTfIAP/zkP6wP
          jYHMRTCaQb7/nB878dLAjUD1THO7yImJ0h5HgRSgOCP0s01ohmLQcDfD0ZItLvu5
          vL6rUQFBggxut6dJyuPLaiWmGEzc1VtsaHAjgyPxAoGBANFP6uXNv/4LpVxq6gpE
          ZAatHT9AcZOKSxDmLzc9QuueQel/Z1Pv6/9zD30G3faLV9ANPX0yrHV8yl6ePfhF
          Qru4MXbYFymQTUbhmhGY6vQqLW/97HX7/4qJYIouyYL+IkHGhB0GLnH0xYYf9cs6
          Wsr6PcKZ0lguUpgyuPO22WvZAoGAb9cY70zijEEtlYdV37PW/wFfJ6LkHQ3yrB2f
          SNXnCTcXh0SVmow7mmxAhUGbWB1+Rf6HZEzg7pHtNUCjnkH9ahz1LsigODqa1ADf
          DK69qHyUYAyhWo+E/pRW+66n+sKZcyakTTNUnDFKH65cofVVdcJuLqa4k45lA2wY
          uLu3USECgYEAg2PIiMrPwLZpDuOODYPnYCuzIctprHCZiNgdPPsXskJwNh+LSxYE
          G382XbV41zqZQTkCOGtSWxa03UrVlFNkrmU3z1pqvDvipbjPpFeNQ65jH48Gv5r7
          7DMu1O5xQK1Z0hNF7Spm2+Y+FIcOR9hRxEYo4a3v+tvHElvawNCjBJg=
          -----END RSA PRIVATE KEY-----
    
      roles:
        - role: ansible-role-consul
        - role: ansible-role-vault

License
-------

MIT

Author Information
------------------

Mark Honomichl aka [AustinCloudGuru](https://austincloud.guru)
Created in 2018
