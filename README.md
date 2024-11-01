
[![Logo](https://www.virtua.cloud/img/logo_48.png)](https://www.virtua.cloud "Cloud Hosting Provider")


    

## Deploy and manage your cloud from your code.

OpenAPI / Swagger API definition file is available : [openapi3_0.yaml](openapi3_0.yaml) [openapi3_0.json](openapi3_0.json).

## Environment Variables

To run this project, you will need to add the following environment variables to your .env file

`API_KEY`

  
## Support

For support, email hello@virtua.cloud.

  
## API Reference

## Display account informations

```http
GET /v1/account
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `API_KEY` | `string` | **Required**. Your API key |

### Example

#### Request

```bash
curl -s --header 'Content-Type: application/json' --request GET -H 'Authorization: Basic API_KEY' 'https://api.virtua.cloud/v1/account'
```
#### Result

```json
{
    "balance":"93.6425",
    "currency":"EUR",
    "monthly_cloud_usage":"6.4590",
    "monthly_cloud_usage_estimate":"37.5633",
    "timezone":"Europe\/Paris",
    "today_cloud_usage":"1.0714",
    "cloud_servers_limit":"8"
}
```

## Display resources usage and limits

```http
GET /v1/cloud/limits
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `API_KEY` | `string` | **Required**. Your API key |

### Example

#### Request

```bash
curl -s --header 'Content-Type: application/json' --request GET -H 'Authorization: Basic API_KEY' 'https://api.virtua.cloud/v1/cloud/limits'
```
#### Result

```json
{
    "success":true,
    "usage":
    {
        "cloud_servers":5,
        "vcpus":"10",
        "memory_size":"18944",
        "root_space":"120",
        "ip_address_v4":"5",
        "ip_address_v6":"3"
    },
    "limits":
    {
        "cloud_servers":"8",
        "smtp_enabled":"1"
    }
}
```

## List all active Cloud Servers

```http
GET /v1/cloud-server
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `API_KEY` | `string` | **Required**. Your API key |

### Example

#### Request

```bash
curl -s --header 'Content-Type: application/json' --request GET -H 'Authorization: Basic API_KEY' 'https://api.virtua.cloud/v1/cloud-server'
```
#### Result

```json
{
    "success":true,
    "cloud_servers":[
        {
            "uuid":"4768103d-7e0b-46c8-8f65-360bcd7b3322",
            "name":"vs4023.par01fr.vsys.cloud",
            "label":null,
            "offer":
            {
                "uuid":"vcs-2-win-ryzen",
                "category":"vcs-win",
                "name":"vCS-2-WIN",
                "price_month":"12.00",
                "price_hour":"0.0164"
            },
            "start_time":"2020-02-10 13:53:53",
            "end_time":"2020-02-10 22:05:01",
            "monthly_usage":"0.134243111111080000000000000000",
            "short_description":null,
            "is_suspended":"0",
            "suspension_reason":null,
            "cloud_zone":
            {
                "country_code":"FR",
                "country_name":"France",
                "city_name":"Paris",
                "datacenter_name":"Iliad DC2",
                "timezone":"Europe\/Paris"
            },
            "vcpus":"2",
            "vcpus_used":"1",
            "memory_size":"4096",
            "memory_size_used":"3597",
            "root_space":"40",
            "root_disk_type":"nvme",
            "status":"running",
            "is_error":"0",
            "is_setup":"1",
            "system":
            {
                "uuid":"win2k19-std-fr-64",
                "name":"Windows Server 2019 Standard (64 bits)"
            },
            "uptime":"14624",
            "vm_type":"qemu",
            "setup_step":null,
            "netboot_on":null,
            "netboot_is_setup":"1",
            "is_smtp_allowed":"1",
            "hostname":null,
            "is_setup_at":"2020-02-10 13:53:53",
            "is_ipv6_enabled":"1",
            "is_processing":"0",
            "ssh_keys":null,
            "keyboard":"fr"
        }
    ]
}
```

## Display a Cloud Server informations

```http
GET /v1/cloud-server/UUID
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `API_KEY` | `string` | **Required**. Your API key |
| `UUID` | `string` | **Required**. Your cloud sever UUID |

### Example

#### Request

```bash
curl -s --header 'Content-Type: application/json' --request GET -H 'Authorization: Basic API_KEY' 'https://api.virtua.cloud/v1/cloud-server/UUID'
```
#### Result

```json
{
    "success":true,
    "uuid":"4768103d-7e0b-46c8-8f65-360bcd7b3322",
    "name":"vs4023.par01fr.vsys.cloud",
    "label":null,
    "offer":
    {
        "uuid":"vcs-2-win-ryzen",
        "category":"vcs-win",
        "name":"vCS-2-WIN",
        "price_month":"12.00",
        "price_hour":"0.0164"
    },
    "start_time":"2020-02-10 13:53:53",
    "end_time":"2020-02-10 22:05:01",
    "monthly_usage":"0.134243111111080000000000000000",
    "short_description":null,
    "is_suspended":"0",
    "suspension_reason":null,
    "cloud_zone":
    {
        "country_code":"FR",
        "country_name":"France",
        "city_name":"Paris",
        "datacenter_name":"Iliad DC2",
        "timezone":"Europe\/Paris"
    },
    "vcpus":"2",
    "vcpus_used":"1",
    "memory_size":"4096",
    "memory_size_used":"3597",
    "root_space":"40",
    "root_disk_type":"nvme",
    "status":"running",
    "is_error":"0",
    "is_setup":"1",
    "system":
    {
        "uuid":"win2k19-std-fr-64",
        "name":"Windows Server 2019 Standard (64 bits)"
    },
    "uptime":"14624",
    "vm_type":"qemu",
    "setup_step":null,
    "netboot_on":null,
    "netboot_is_setup":"1",
    "is_smtp_allowed":"1",
    "hostname":null,
    "is_setup_at":"2020-02-10 13:53:53",
    "is_ipv6_enabled":"1",
    "is_processing":"0",
    "ssh_keys":null,
    "keyboard":"fr"
}
```

## Start a Cloud Server

```http
POST /v1/cloud-server/UUID/start
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `API_KEY` | `string` | **Required**. Your API key |
| `UUID` | `string` | **Required**. Your cloud sever UUID |

### Example

#### Request

```bash
curl -s --header 'Content-Type: application/json' --request POST -H 'Authorization: Basic API_KEY' 'https://api.virtua.cloud/v1/cloud-server/UUID/start'
```
#### Result

```json
{
    "success":true,
    "uuid":"UUID",
    "messages":[
        {
            "content":"Start in progress...",
            "type":"notice"
        }
    ]
}
```

## Stop a Cloud Server

```http
POST /v1/cloud-server/UUID/stop
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `API_KEY` | `string` | **Required**. Your API key |
| `UUID` | `string` | **Required**. Your cloud sever UUID |

### Example

#### Request

```bash
curl -s --header 'Content-Type: application/json' --request POST -H 'Authorization: Basic API_KEY' 'https://api.virtua.cloud/v1/cloud-server/UUID/stop'
```
#### Result

```json
{
    "success":true,
    "uuid":"UUID",
    "messages":[
        {
            "content":"Stop in progress...",
            "type":"notice"
        }
    ]
}
```

## Restart a Cloud Server

```http
POST /v1/cloud-server/UUID/restart
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `API_KEY` | `string` | **Required**. Your API key |
| `UUID` | `string` | **Required**. Your cloud sever UUID |

### Example

#### Request

```bash
curl -s --header 'Content-Type: application/json' --request POST -H 'Authorization: Basic API_KEY' 'https://api.virtua.cloud/v1/cloud-server/UUID/restart'
```
#### Result

```json
{
    "success":true,
    "uuid":"UUID",
    "messages":[
        {
            "content":"Restart in progress...",
            "type":"notice"
        }
    ]
}
```

## Resize a Cloud Server

```http
POST /v1/cloud-server/UUID/resize
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `API_KEY` | `string` | **Required**. Your API key |
| `UUID` | `string` | **Required**. Your cloud sever UUID |
| `NEW_OFFER_UUID` | `string` | **Required**. The new offer UUID |
| `resize_disk` | `boolean` | **Required**. 1 upgrade the disk size, 0 keep the disk size unchanged |

### Example

#### Request

```bash
curl -s --header 'Content-Type: application/json' --request POST -H 'Authorization: Basic API_KEY' 'https://api.virtua.cloud/v1/cloud-server/UUID/resize' --data 'offer=NEW_OFFER_UUID' -d 'resize_disk=1'
```
#### Result

```json
{
    "success":true,
    "uuid":"UUID",
    "messages":[
        {
            "content":"Update in progress...",
            "type":"notice"
        }
    ]
}
```

## Rebuild a Cloud Server

```http
POST /v1/cloud-server/UUID/rebuild
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `API_KEY` | `string` | **Required**. Your API key |
| `UUID` | `string` | **Required**. Your cloud sever UUID |
| `system` | `string` | System UUID |
| `iso_image` | `string` | ISO Image UUID |

### Example

#### Request

```bash
curl -s --header 'Content-Type: application/json' --request POST -H 'Authorization: Basic API_KEY' 'https://api.virtua.cloud/v1/cloud-server/UUID/rebuild'
```
#### Result

```json
{
    "success":true,
    "uuid":"UUID",
    "messages":[
        {
            "content":"Reinstall in progress...",
            "type":"notice"
        }
    ]
}
```

## Destroy a Cloud Server

```http
DELETE /v1/cloud-server/UUID
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `API_KEY` | `string` | **Required**. Your API key |
| `UUID` | `string` | **Required**. Your cloud sever UUID |

### Example

#### Request

```bash
curl -s --header 'Content-Type: application/json' --request DELETE -H 'Authorization: Basic API_KEY' 'https://api.virtua.cloud/v1/cloud-server/UUID'
```
#### Result

```json
{
    "success":true,
    "uuid":"UUID",
    "messages":[
        {
            "content":"Server destroyed.",
            "type":"notice"
        }
    ]
}
```

## Deploy a new Cloud Server

```http
POST /v1/cloud/order
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `API_KEY` | `string` | **Required**. Your API key |
| `PROJECT_UUID` | `string` | **Required**. Project UUID |
| `OFFER_UUID` | `string` | **Required**. Offer UUID |
| `SYSTEM_UUID` | `string` | **Required**. System UUID |
| `ipv6_enabled` | `boolean` | **Required**. 1 enable and addign a IPv6, 0 disable IPv6 and no IPv6 assignation |
| `ipv6_block_size` | `integer` | 128 for one IPv6, 64 for a block |
| `hostname` | `string` | A custom hostname |


### Example

#### Request

```bash
curl -s --header 'Content-Type: application/json' --request POST -H 'Authorization: Basic API_KEY' 'https://api.virtua.cloud/v1/cloud/order' --data 'offer=OFFER_UUID' -d 'system=SYSTEM_UUID' -d 'ipv6_enable=0' -d 'hostname=my.server.cloud' -d 'project=PROJECT_UUID'
```
#### Result

```json
{
    "success":true,
    "uuid":"UUID",
}
```

## Display Offers

```http
GET /v1/cloud/offers
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `API_KEY` | `string` | **Required**. Your API key |

### Example

#### Request

```bash
curl -s --header 'Content-Type: application/json' --request GET -H 'Authorization: Basic API_KEY' 'https://api.virtua.cloud/v1/cloud/offers'
```
#### Result

```json
{
   "success":true,
   "offers":[
      {
         "uuid":"vcs-2-intel.par01fr",
         "category":"vcs",
         "name":"vCS-2",
         "price_month":"12.00",
         "price_hour":"0.0167",
         "additional_root_space_price_month":"1.80",
         "additional_root_space_price_hour":"0.00000070",
         "vcpus":"1",
         "cpu_family":"intel-xeon",
         "memory_size":"2048",
         "root_space":"40",
         "root_disk_type":"ssd",
         "bandwidth":"100",
         "is_windows_included":"0",
         "additional_ipv4_addresses_max":"4",
         "additional_ipv4_addresses_price_hour":"0.00347000",
         "additional_ipv4_addresses_price_month":"2.50",
         "cloud_zone":{
            "country_code":"FR",
            "country_name":"France",
            "city_name":"Paris",
            "datacenter_name":"Iliad DC2",
            "timezone":"Europe\/Paris"
         }
      }
   ]
}
```

## Display Systems

```http
GET /v1/cloud/systems
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `API_KEY` | `string` | **Required**. Your API key |

### Example

#### Request

```bash
curl -s --header 'Content-Type: application/json' --request GET -H 'Authorization: Basic API_KEY' 'https://api.virtua.cloud/v1/cloud/systems'
```
#### Result

```json
{
   "success":true,
   "systems":[
      {
         "uuid":"debian-10-64",
         "name":"Debian 10 (64 bits)",
         "distribution":"debian",
         "version":"10",
         "category":"minimal",
         "is_windows":"0"
      },
      {
         "uuid":"centos-7-64",
         "name":"Centos 7 (64 bits)",
         "distribution":"centos",
         "version":"7",
         "category":"minimal",
         "is_windows":"0"
      },
      {
         "uuid":"archlinux-latest-64",
         "name":"ArchLinux Latest (64 bits)",
         "distribution":"archlinux",
         "version":"0",
         "category":"minimal",
         "is_windows":"0"
      },
      {
         "uuid":"win2k19-std-fr-64",
         "name":"Windows Server 2019 Standard (64 bits)",
         "distribution":"windows-server-2019",
         "version":"2019",
         "category":"windows",
         "is_windows":"1"
      },
      {
         "uuid":"win2k19-std-en-64",
         "name":"Windows Server 2019 Standard (64 bits)",
         "distribution":"windows-server-2019",
         "version":"2019",
         "category":"windows",
         "is_windows":"1"
      }
   ]
}
```
