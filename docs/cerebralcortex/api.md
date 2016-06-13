# Cerebral Cortex API Reference

## Header information
All POST resquests must specify:
`Content-Type: application/josn`


## Workflow for Cerebral Cortex API
JSON API

### Register Participant
**URL:** `https://cerebralcortex/participants`

Request: POST
```JSON
{
    "identifier": "Participant Name/Identifier"
}
```

## Register Study
**URL:** `https://cerebralcortex/studies`

Request: POST
```JSON
{
    "identifier": "Study XYZ",
    "name": "Study Name"
}
```

### Register Participant in Study
**URL:** `https://cerebralcortex/studies/register_participant`

Request: POST
```JSON
{
    "participant_id": "b1c966b4-06c8-4ebd-9aee-67bcfd38d0d6",
    "study_id": 4
}
```

### Register Data Source
**URL:** `https://cerebralcortex/datasources/register`

Request: POST
```JSON
{
    "participant_id": "b1c966b4-06c8-4ebd-9aee-67bcfd38d0d6",
    "datasource": {
        "type": "MEMORY",
        "platform": {
            "type": "PHONE",
            "metadata": {
                "OPERATING_SYSTEM": "5.1.1",
                "MODEL": "SAMSUNG-SM-G900A",
                "MANUFACTURER": "samsung",
                "NAME": "Phone"
            }
        },
        "application": {
            "id": "org.md2k.phonesensor",
            "metadata": {
                "VERSION_NAME": "0.8.0",
                "VERSION_NUMBER": "11"
            }
        },
        "dataDescriptors": [
            {
                "UNIT": "megabyte",
                "DESCRIPTION": "Size of the memory",
                "FREQUENCY": "1.0 Hz",
                "MAX_VALUE": "2048",
                "MIN_VALUE": "0",
                "DATA_TYPE": "float",
                "NAME": "Size"
            },
            {
                "UNIT": "megabyte",
                "DESCRIPTION": "Available memory",
                "FREQUENCY": "1.0 Hz",
                "MAX_VALUE": "2048",
                "MIN_VALUE": "0",
                "DATA_TYPE": "float",
                "NAME": "Available"
            }
        ],
        "metadata": {
            "DESCRIPTION": "measures usage of memory",
            "FREQUENCY": "1.0 Hz",
            "DATA_TYPE": "org.md2k.datakitapi.datatype.DataTypeFloatArray",
            "NAME": "Memory"
        }
    }
}
```

### Load data for each data stream
**URL:** `https://cerebralcortex/datapoints/bulkload` or `https://cerebralcortex/rawdatapoints/bulkload`

Request: POST
```JSON
{
    "datastream_id": 5,
    "data": [
        {
            "dateTime": 1455862218000,
            "offset": -21600000,
            "sample": [1,2,3,4]
        },
        {
            "dateTime": 1455862219000,
            "offset": -21600000,
            "sample": [
                {
                    "foo":"bar"
                },
                {
                    "foo":"bar"
                }
            ]
        }
    ]
}
```



## Participant registration
JSON API for participant registration

Request fields

* `identifier`: String identifier
* `id` (optional): UUID of this form: a37fbcab-0f90-4dd3-907d-f0cb3f247302

Response fields

* `identifier`: String
* `id`: UUID
* `created_at`: DateTime
* `updated_at`: DateTime


### Example

**URL:** `https://cerebralcortex/participants`

Request: POST
```JSON
{
    "identifier": "Participant Name/Identifier"
}
```

_Response_

```JSON
{
  "id": "a37fbcab-0f90-4dd3-907d-f0cb3f247302",
  "identifier": "Participant Name/Identifier",
  "created_at": "2016-04-28T01:56:38.217Z",
  "updated_at": "2016-04-28T01:56:38.217Z"
}
```

### Example

**URL:** `https://cerebralcortex/participants`

Request: POST
```JSON
{
    "identifier": "Participant Name/Identifier",
    "id": "a37fbcab-0f90-4dd3-907d-f0cb3f247302"
}
```

_Response_
```JSON
{
  "id": "a37fbcab-0f90-4dd3-907d-f0cb3f247302",
  "identifier": "Participant Name/Identifier",
  "created_at": "2016-04-28T01:56:38.217Z",
  "updated_at": "2016-04-28T01:56:38.217Z"
}
```


## Study registration
JSON API for study registration

Request Fields

* `identifier`: String identifier (typically a study or protocol number)
* `name`: Human readable study name

_Response fields_

* `id`: Integer
* `identifier`: String
* `name`: String
* `created_at`: DateTime
* `updated_at`: DateTime


### Example

**URL:** `https://cerebralcortex/studies`

Request: POST
```JSON
{
    "identifier": "Study XYZ",
    "name": "Study Name"
}
```
_Response_
```JSON
{
  "id": 4,
  "identifier": "Study XYZ",
  "name": "Study Name",
  "created_at": "2016-04-18T20:09:00.286Z",
  "updated_at": "2016-04-18T20:09:00.286Z"
}
```



## Participant-Study registration
JSON API for registering an existing participant in and existing study

Request Fields

* `participant_id`: UUID from `participant_registration.id` response
* `study_id`: Integer from `study_registration.id` response

_Response fields_

* `id`: Integer
* `participant_id`: UUID
* `study_id`: Integer
* `created_at`: DateTime
* `updated_at`: DateTime


### Example

**URL:** `https://cerebralcortex/studies`

Request: POST
```JSON
{
    "participant_id": "b1c966b4-06c8-4ebd-9aee-67bcfd38d0d6",
    "study_id": 4
}
```

_Response_
```JSON
{
  "id": 19,
  "participant_id": "b1c966b4-06c8-4ebd-9aee-67bcfd38d0d6",
  "study_id": 4,
  "created_at": "2016-04-28T02:15:04.213Z",
  "updated_at": "2016-04-28T02:15:04.213Z"
}
```



## Datasource registration
JSON API for data source registration

Request Structure
```JSON
{
    "participant_id": UUID,
    "datasource": {
        "type": String,
        "id" (optional): String,
        "metadata" (optional): JsonObject representing a ,
        "platform" (optional): {
            "type": String,
            "id": String,
            "metadata": JsonObject representing a HashMap
        },
        "application" (optional): {
            "type": String,
            "id": String,
            "metadata": JsonObject representing a
        },
        "platform" (optional): {
            "type": String,
            "id": String,
            "metadata": JsonObject representing a
        },
        "platformapp" (optional): {
            "type": String,
            "id": String,
            "metadata": JsonObject representing a
        },
        "dataDescriptors" (optional): [
            {
                JsonObject for each item in the datapoint sample
            },
            ...
        ]
    }
}
```

_Response fields_

* `status`: Enum: (OK, ERROR)
* `message`: String
* `datastream_id`: Integer


### Example

**URL:** `https://cerebralcortex/datasources/register`

Request: POST
```JSON
{
    "participant_id": "b1c966b4-06c8-4ebd-9aee-67bcfd38d0d6",
    "datasource": {
        "type": "MEMORY",
        "platform": {
            "type": "PHONE",
            "metadata": {
                "OPERATING_SYSTEM": "5.1.1",
                "MODEL": "SAMSUNG-SM-G900A",
                "MANUFACTURER": "samsung",
                "NAME": "Phone"
            }
        },
        "application": {
            "id": "org.md2k.phonesensor",
            "metadata": {
                "VERSION_NAME": "0.8.0",
                "VERSION_NUMBER": "11"
            }
        },
        "dataDescriptors": [
            {
                "UNIT": "megabyte",
                "DESCRIPTION": "Size of the memory",
                "FREQUENCY": "1.0 Hz",
                "MAX_VALUE": "2048",
                "MIN_VALUE": "0",
                "DATA_TYPE": "float",
                "NAME": "Size"
            },
            {
                "UNIT": "megabyte",
                "DESCRIPTION": "Available memory",
                "FREQUENCY": "1.0 Hz",
                "MAX_VALUE": "2048",
                "MIN_VALUE": "0",
                "DATA_TYPE": "float",
                "NAME": "Available"
            }
        ],
        "metadata": {
            "DESCRIPTION": "measures usage of memory",
            "FREQUENCY": "1.0 Hz",
            "DATA_TYPE": "org.md2k.datakitapi.datatype.DataTypeFloatArray",
            "NAME": "Memory"
        }
    }
}
```

_Response_
```JSON
{
  "status": "ok",
  "message": "Successfully loaded datasource",
  "datastream_id": "908"
}
```



## Data point bulk loader
JSON API for data point bulk loading

The URL determines where data is persisted.

* Postgresql (datapoints)
* Postgresql and Cassandra (rawdatapoints)

Request Structure
```JSON
{
    "datastream_id": Integer from datasource_registration process,
    "data": [
        {
            "dateTime": Long milliseconds since 1970,
            "offset": Long offset in milliseconds from UTC to current timezone,
            "sample": Array of JsonObjects
        },
        ...
    ]
}
```

_Response fields_

* `status`: Enum: (OK, ERROR)
* `message`: String
* `count`: Integer indicating number of entries processed


### Example

**URL:** `https://cerebralcortex/datapoints/bulkload` or `https://cerebralcortex/rawdatapoints/bulkload`

Request: POST
```JSON
{
    "datastream_id": 5,
    "data": [
        {
            "dateTime": 1455862218000,
            "offset": -21600000,
            "sample": [1,2,3,4]
        },
        {
            "dateTime": 1455862219000,
            "offset": -21600000,
            "sample": [
                {
                    "foo":"bar"
                },
                {
                    "foo":"bar"
                }
            ]
        }
    ]
}
```

_Response_
```JSON
{
  "status": "ok",
  "message": "Successfully loaded datapoints",
  "count": 2
}
```
