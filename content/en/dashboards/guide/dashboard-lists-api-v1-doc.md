---
title: Dashboard Lists API (v1)
kind: guide
aliases:
  - /graphing/faq/dashboard-lists-api-doc
  - /graphing/guide/dashboard-lists-api-v1-doc
---

Interact with your dashboard lists through the API to make it easier to organize, find, and share all of your dashboards with your team and organization.

- [Get items of a dashboard list](#get-items-of-a-dashboard-list)
- [Add items to a dashboard list](#add-items-to-a-dashboard-list)
- [Update items of a dashboard list](#update-items-of-a-dashboard-list)
- [Delete items from a dashboard list](#delete-items-from-a-dashboard-list)

## Get items of a dashboard list

<div class="alert alert-danger">
This endpoint is outdated. Use the <a href="https://docs.datadoghq.com/api#get-items-of-a-dashboard-list">get items of a dashboard list v2 endpoint</a> instead.
</div>

### Signature

`GET https://api.datadoghq.com/api/v1/dashboard/lists/manual/<LIST_ID>/dashboards`

### Examples

#### Example request

{{< tabs >}}
{{% tab "Python" %}}

```python
from datadog import initialize, api

options = {
    'api_key': '<DATADOG_API_KEY>',
    'app_key': '<DATADOG_APPLICATION_KEY>'
}

initialize(**options)

api.DashboardList.get_items(4741)

```

{{% /tab %}}
{{% tab "Ruby" %}}

```ruby
require 'rubygems'
require 'dogapi'

api_key = '<DATADOG_API_KEY>'
app_key = '<DATADOG_APPLICATION_KEY>'

dog = Dogapi::Client.new(api_key, app_key)

result = dog.get_items_of_dashboard_list(4741)
```

{{% /tab %}}
{{% tab "Curl" %}}

```sh
api_key=<DATADOG_API_KEY>
app_key=<DATADOG_APPLICATION_KEY>

list_id=4741

curl -X GET \
"https://api.datadoghq.com/api/v1/dashboard/lists/manual/${list_id}/dashboards?api_key=${api_key}&application_key=${app_key}"
```

{{% /tab %}}
{{< /tabs >}}

#### Example response

{{< tabs >}}
{{% tab "Python" %}}

```python
{
    'total': 5,
    'dashboards': [
        {
            'is_shared': False,
            'author': {
                'handle': None,
                'name': None
            },
            'url': '/screen/integration/66/aws-dynamodb',
            'title': 'Amazon DynamoDB',
            'modified': None,
            'created': None,
            'is_favorite': True,
            'is_read_only': True,
            'type': 'integration_screenboard',
            'id': 66,
            'icon': '/static/v/34.254868/images/saas_logos/small/amazon_dynamodb.png'
        },
        {
            'is_shared': False,
            'author': {
                'handle': None,
                'name': None
            },
            'url': '/dash/integration/17/postgres---metrics',
            'title': 'Postgres - Metrics',
            'modified': None,
            'created': None,
            'is_favorite': True,
            'is_read_only': True,
            'type': 'integration_timeboard',
            'id': 17,
            'icon': '/static/v/34.254868/images/saas_logos/small/postgres.png'
        },
        {
            'new_id': 'qts-q2k-yq6',
            'popularity': 0,
            'is_shared': False,
            'author': {
                'handle': 'test1@datadoghq.com',
                'name': 'Author Name'
            },
            'url': '/dash/75619/trace-api',
            'title': 'Trace API',
            'modified': '2018-03-16T13:39:39.517133+00:00',
            'created': '2015-10-21T13:22:48.633391+00:00',
            'is_favorite': False,
            'is_read_only': False,
            'type': 'custom_timeboard',
            'id': 75619,
            'icon': None
        },
        {
            'new_id': 'rys-xwq-geh',
            'popularity': 0,
            'is_shared': False,
            'author': {
                'handle': 'test2@datadoghq.com',
                'name': 'Other Author Name'
            },
            'url': '/screen/63572/agent-stats',
            'title': 'Agent Stats',
            'modified': '2018-03-16T12:54:25.968134+00:00',
            'created': '2014-06-18T18:19:00.974763+00:00',
            'is_favorite': False,
            'is_read_only': False,
            'type': 'custom_screenboard',
            'id': 63572
            'icon': None
        },
        {
            'popularity': 0,
            'is_shared': False,
            'author': {
                'handle': None,
                'name': None
            },
            'url': '/dash/host/3245468',
            'title': 'agent-gui',
            'modified': None,
            'created': None,
            'is_favorite': False,
            'is_read_only': True,
            'type': 'host_timeboard',
            'id': 3245468,
            'icon': None
        }
    ]
}
```

{{% /tab %}}
{{% tab "Ruby" %}}

```ruby
[
    "200",
    {
        "total" => 5,
        "dashboards" => [
            {
                "title" => "Amazon DynamoDB",
                "is_favorite" => true,
                "id" => 66,
                "icon" => "/static/v/34.254868/images/saas_logos/small/amazon_dynamodb.png",
                "is_shared" => false,
                "author" => {
                    "handle" => nil,
                    "name" => nil
                },
                "url" => "/screen/integration/66/aws-dynamodb",
                "created" => nil,
                "modified" => nil,
                "is_read_only" => true,
                "type" => "integration_screenboard"
            },
            {
                "title" => "Postgres - Metrics",
                "is_favorite" => true,
                "id" => 17,
                "icon" => "/static/v/34.254868/images/saas_logos/small/postgres.png",
                "is_shared" => false,
                "author" => {
                    "handle" => nil,
                    "name" => nil
                },
                "url" => "/dash/integration/17/postgres---metrics",
                "created" => nil,
                "modified" => nil,
                "is_read_only" => true,
                "type" => "integration_timeboard"
            },
            {
                "new_id" => "qts-q2k-yq6",
                "popularity" => 0,
                "title" => "Trace API",
                "is_favorite" => false,
                "id" => 75619,
                "icon" => nil,
                "is_shared" => false,
                "author" => {
                    "handle" => "test1@datadoghq.com",
                    "name" => "Author Name"
                },
                "url" => "/dash/75619/trace-api",
                "created" => "2015-10-21T13:22:48.633391+00:00",
                "modified" => "2018-03-16T13:39:39.517133+00:00",
                "is_read_only" => false,
                "type" => "custom_timeboard"
            },
            {
                "new_id" => "rys-xwq-geh",
                "popularity" => 0,
                "title" => "Agent Stats",
                "is_favorite" => false,
                "id" => 63572,
                "icon" => nil,
                "is_shared" => false,
                "author" => {
                    "handle" => "test2@datadoghq.com",
                    "name" => "Other Author Name"
                },
                "url" => "/screen/63572/agent-stats",
                "created" => "2014-06-18T18:19:00.974763+00:00",
                "modified" => "2018-03-16T12:54:25.968134+00:00",
                "is_read_only" => false,
                "type" => "custom_screenboard"
            },
            {
                "popularity" => 0,
                "title" => "agent-gui",
                "is_favorite" => false,
                "id" => 3245468,
                "icon" => nil,
                "is_shared" => false,
                "author" => {
                    "handle" => nil,
                    "name" => nil
                },
                "url" => "/dash/host/3245468",
                "created" => nil,
                "modified" => nil,
                "is_read_only" => true,
                "type" => "host_timeboard"
            }
        ]
    }
]

```

{{% /tab %}}
{{% tab "Curl" %}}

```sh
{
    "total": 5,
    "dashboards": [
        {
            "is_shared": False,
            "author": {
                "handle": None,
                "name": None
            },
            "url": "/screen/integration/66/aws-dynamodb",
            "title": "Amazon DynamoDB",
            "modified": None,
            "created": None,
            "is_favorite": True,
            "is_read_only": True,
            "type": "integration_screenboard",
            "id": 66,
            "icon": "/static/v/34.254868/images/saas_logos/small/amazon_dynamodb.png"
        },
        {
            "is_shared": False,
            "author": {
                "handle": None,
                "name": None
            },
            "url": "/dash/integration/17/postgres---metrics",
            "title": "Postgres - Metrics",
            "modified": None,
            "created": None,
            "is_favorite": True,
            "is_read_only": True,
            "type": "integration_timeboard",
            "id": 17,
            "icon": "/static/v/34.254868/images/saas_logos/small/postgres.png"
        },
        {
            "new_id": "qts-q2k-yq6",
            "popularity": 0,
            "is_shared": False,
            "author": {
                "handle": "test1@datadoghq.com",
                "name": "Author Name"
            },
            "url": "/dash/75619/trace-api",
            "title": "Trace API",
            "modified": "2018-03-16T13:39:39.517133+00:00",
            "created": "2015-10-21T13:22:48.633391+00:00",
            "is_favorite": False,
            "is_read_only": False,
            "type": "custom_timeboard",
            "id": 75619,
            "icon": None
        },
        {
            "new_id": "rys-xwq-geh",
            "popularity": 0,
            "is_shared": False,
            "author": {
                "handle": "test2@datadoghq.com",
                "name": "Other Author Name"
            },
            "url": "/screen/63572/agent-stats",
            "title": "Agent Stats",
            "modified": "2018-03-16T12:54:25.968134+00:00",
            "created": "2014-06-18T18:19:00.974763+00:00",
            "is_favorite": False,
            "is_read_only": False,
            "type": "custom_screenboard",
            "id": 63572,
            "icon": None
        },
        {
            "popularity": 0,
            "is_shared": False,
            "author": {
                "handle": None,
                "name": None
            },
            "url": "/dash/host/3245468",
            "title": "agent-gui",
            "modified": None,
            "created": None,
            "is_favorite": False,
            "is_read_only": True,
            "type": "host_timeboard",
            "id": 3245468,
            "icon": None
        }
    ]
}

```

{{% /tab %}}
{{< /tabs >}}

## Add items to a dashboard list

<div class="alert alert-danger">
This endpoint is outdated. Use the <a href="https://docs.datadoghq.com/api#add-items-to-a-dashboard-list">add items to a dashboard list v2 endpoint</a> instead.
</div>

### Signature

`POST https://api.datadoghq.com/api/v1/dashboard/lists/manual/<LIST_ID>/dashboards`

### Arguments

*   **`dashboards`** [*required*]:
    A list of dashboards to add to the list.
    Dashboard definitions follow this form:
    *   **`type`** [*required*]:
        The type of the dashboard.
        The type must be one of:

        * `"custom_timeboard"`
        * `"custom_screenboard"`
        * `"integration_screenboard"`
        * `"integration_timeboard"`
        * `"host_timeboard"`
    *   **`id`** [*required*]:
        The id of the dashboard.

### Examples

#### Example request

{{< tabs >}}
{{% tab "Python" %}}

```python
from datadog import initialize, api

options = {
    'api_key': '<DATADOG_API_KEY>',
    'app_key': '<DATADOG_APPLICATION_KEY>'
}

initialize(**options)

list_id = 4741
dashboards = [
    {
        'type': 'custom_screenboard',
        'id': 1414
    },
    {
        'type': 'custom_timeboard',
        'id': 5858
    },
    {
        'type': 'integration_screenboard',
        'id': 67
    },
    {
        'type': 'integration_timeboard',
        'id': 5
    },
    {
        'type': 'host_timeboard',
        'id': 123456789
    }
]

api.DashboardList.add_items(list_id, dashboards=dashboards)

```

{{% /tab %}}
{{% tab "Ruby" %}}

```ruby
require 'rubygems'
require 'dogapi'

api_key = '<DATADOG_API_KEY>'
app_key = '<DATADOG_APPLICATION_KEY>'

dog = Dogapi::Client.new(api_key, app_key)

list_id = 4741
dashboards = [
    {
        "type" => "custom_screenboard",
        "id" => 1414
    },
    {
        "type" => "custom_timeboard",
        "id" => 5858
    },
    {
        "type" => "integration_screenboard",
        "id" => 67
    },
    {
        "type" => "integration_timeboard",
        "id" => 5
    },
    {
        "type" => "host_timeboard",
        "id" => 123456789
    }
]

result = dog.add_items_of_dashboard_list(list_id, dashboards)
```

{{% /tab %}}
{{% tab "Curl" %}}

```sh
api_key=<DATADOG_API_KEY>
app_key=<DATADOG_APPLICATION_KEY>

list_id=4741

curl -X ADD -H "Content-type: application/json" \
-d '{
        "dashboards": [
            {
                "type": "custom_screenboard",
                "id": 1414
            },
            {
                "type": "custom_timeboard",
                "id": 5858
            },
            {
                "type": "integration_screenboard",
                "id": 67
            },
            {
                "type": "integration_timeboard",
                "id": 5
            },
            {
                "type": "host_timeboard",
                "id": 123456789
            }
        ]
}' \
"https://api.datadoghq.com/api/v1/dashboard/lists/manual/${list_id}/dashboards?api_key=${api_key}&application_key=${app_key}"
```

{{% /tab %}}
{{< /tabs >}}

#### Example response

{{< tabs >}}
{{% tab "Python" %}}

```python
{
    'added_dashboards_to_list': [
        {
            'type': 'custom_timeboard',
            'id': 5858
        },
        {
            'type': 'custom_screenboard',
            'id': 1414
        },
        {
            'type': 'integration_timeboard',
            'id': 5
        },
        {
            'type': 'integration_screenboard',
            'id': 67
        },
        {
            'type': 'host_timeboard',
            'id': 123456789
        }
    ]
}
```

{{% /tab %}}
{{% tab "Ruby" %}}

```ruby
[
    "200",
    {
        "dashboards" => [
            {
                "type" => "custom_timeboard",
                "id" => 5858
            },
            {
                "type" => "custom_screenboard",
                "id" => 1414
            },
            {
                "type" => "integration_timeboard",
                "id" => 5
            },
            {
                "type" => "integration_screenboard",
                "id" => 67
            },
            {
                "type" => "host_timeboard",
                "id" => 123456789
            }
        ]
    }
]

```

{{% /tab %}}
{{% tab "Curl" %}}

```sh
{
    "deleted_dashboards_from_list": [
        {
            "type": "custom_timeboard",
            "id": 5858
        },
        {
            "type": "custom_screenboard",
            "id": 1414
        },
        {
            "type": "integration_timeboard",
            "id": 5
        },
        {
            "type": "integration_screenboard",
            "id": 67
        },
        {
            "type": "host_timeboard",
            "id": 123456789
        }
    ]
}

```

{{% /tab %}}
{{< /tabs >}}

## Update items of a dashboard list

<div class="alert alert-danger">
This endpoint is outdated. Use the <a href="https://docs.datadoghq.com/api#update-items-of-a-dashboard-list">update items of a dashboard list v2 endpoint</a> instead.
</div>

### Signature

`PUT https://api.datadoghq.com/api/v1/dashboard/lists/manual/<LIST_ID>/dashboards`

### Arguments

*   **`dashboards`** [*required*]:
    The new list of dashboards for the dashboard list.
    Dashboard definitions follow this form:
    *   **`type`** [*required*]:
        The type of the dashboard.
        The type must be one of:

        * `"custom_timeboard"`
        * `"custom_screenboard"`
        * `"integration_screenboard"`
        * `"integration_timeboard"`
        * `"host_timeboard"`
    *   **`id`** [*required*]:
        The id of the dashboard.

### Examples

#### Example request

{{< tabs >}}
{{% tab "Python" %}}

``` python
from datadog import initialize, api

options = {
    'api_key': '<DATADOG_API_KEY>',
    'app_key': '<DATADOG_APPLICATION_KEY>'
}

initialize(**options)

list_id = 4741
dashboards = [
    {
        'type': 'custom_screenboard',
        'id': 1414
    },
    {
        'type': 'custom_timeboard',
        'id': 5858
    },
    {
        'type': 'integration_screenboard',
        'id': 67
    },
    {
        'type': 'integration_timeboard',
        'id': 5
    },
    {
        'type': 'host_timeboard',
        'id': 123456789
    }
]

api.DashboardList.update_items(list_id, dashboards=dashboards)

```

{{% /tab %}}
{{% tab "Ruby" %}}

``` ruby
require 'rubygems'
require 'dogapi'

api_key = '<DATADOG_API_KEY>'
app_key = '<DATADOG_APPLICATION_KEY>'

dog = Dogapi::Client.new(api_key, app_key)

list_id = 4741
dashboards = [
    {
        "type" => "custom_screenboard",
        "id" => 1414
    },
    {
        "type" => "custom_timeboard",
        "id" => 5858
    },
    {
        "type" => "integration_screenboard",
        "id" => 67
    },
    {
        "type" => "integration_timeboard",
        "id" => 5
    },
    {
        "type" => "host_timeboard",
        "id" => 123456789
    }
]

result = dog.update_items_of_dashboard_list(list_id, dashboards)

```

{{% /tab %}}
{{% tab "Curl" %}}

```sh

api_key=<DATADOG_API_KEY>
app_key=<DATADOG_APPLICATION_KEY>

list_id=4741

curl -X UPDATE -H "Content-type: application/json" \
-d '{
        "dashboards": [
            {
                "type": "custom_screenboard",
                "id": 1414
            },
            {
                "type": "custom_timeboard",
                "id": 5858
            },
            {
                "type": "integration_screenboard",
                "id": 67
            },
            {
                "type": "integration_timeboard",
                "id": 5
            },
            {
                "type": "host_timeboard",
                "id": 123456789
            }
        ]
}' \
"https://api.datadoghq.com/api/v1/dashboard/lists/manual/${list_id}/dashboards?api_key=${api_key}&application_key=${app_key}"

```

{{% /tab %}}
{{< /tabs >}}

##### Example response

{{< tabs >}}
{{% tab "Python" %}}

```python
{
    'dashboards': [
        {
            'type': 'custom_timeboard',
            'id': 5858
        },
        {
            'type': 'custom_screenboard',
            'id': 1414
        },
        {
            'type': 'integration_timeboard',
            'id': 5
        },
        {
            'type': 'integration_screenboard',
            'id': 67
        },
        {
            'type': 'host_timeboard',
            'id': 123456789
        }
    ]
}

```

{{% /tab %}}
{{% tab "Ruby" %}}

```ruby
[
    "200",
    {
        "dashboards" => [
            {
                "type" => "custom_timeboard",
                "id" => 5858
            },
            {
                "type" => "custom_screenboard",
                "id" => 1414
            },
            {
                "type" => "integration_timeboard",
                "id" => 5
            },
            {
                "type" => "integration_screenboard",
                "id" => 67
            },
            {
                "type" => "host_timeboard",
                "id" => 123456789
            }
        ]
    }
]
```

{{% /tab %}}
{{% tab "Curl" %}}

```sh
{
    "deleted_dashboards_from_list": [
        {
            "type": "custom_timeboard",
            "id": 5858
        },
        {
            "type": "custom_screenboard",
            "id": 1414
        },
        {
            "type": "integration_timeboard",
            "id": 5
        },
        {
            "type": "integration_screenboard",
            "id": 67
        },
        {
            "type": "host_timeboard",
            "id": 123456789
        }
    ]
}
```

{{% /tab %}}
{{< /tabs >}}

## Delete items from a dashboard list

<div class="alert alert-danger">
This endpoint is outdated. Use the <a href="https://docs.datadoghq.com/api#delete-items-from-a-dashboard-list">delete items from a dashboard list v2 endpoint</a> instead.
</div>

### Signature

`DELETE https://api.datadoghq.com/api/v1/dashboard/lists/manual/<LIST_ID>/dashboards`

### Arguments

*   **`dashboards`** [*required*]:
    A list of dashboards to remove from the list.
    Dashboard definitions follow this form:
    *   **`type`** [*required*]:
        The type of the dashboard.
        The type must be one of:

        * `"custom_timeboard"`
        * `"custom_screenboard"`
        * `"integration_screenboard"`
        * `"integration_timeboard"`
        * `"host_timeboard"`
    *   **`id`** [*required*]:
        The id of the dashboard.

### Examples

#### Example request

{{< tabs >}}
{{% tab "Python" %}}

``` python
from datadog import initialize, api

options = {
    'api_key': '<DATADOG_API_KEY>',
    'app_key': '<DATADOG_APPLICATION_KEY>'
}

initialize(**options)

list_id = 4741
dashboards = [
    {
        'type': 'custom_screenboard',
        'id': 1414
    },
    {
        'type': 'custom_timeboard',
        'id': 5858
    },
    {
        'type': 'integration_screenboard',
        'id': 67
    },
    {
        'type': 'integration_timeboard',
        'id': 5
    },
    {
        'type': 'host_timeboard',
        'id': 123456789
    }
]

api.DashboardList.delete_items(list_id, dashboards=dashboards)

```

{{% /tab %}}
{{% tab "Ruby" %}}

``` ruby
require 'rubygems'
require 'dogapi'

api_key = '<DATADOG_API_KEY>'
app_key = '<DATADOG_APPLICATION_KEY>'

dog = Dogapi::Client.new(api_key, app_key)

list_id = 4741
dashboards = [
    {
        "type" => "custom_screenboard",
        "id" => 1414
    },
    {
        "type" => "custom_timeboard",
        "id" => 5858
    },
    {
        "type" => "integration_screenboard",
        "id" => 67
    },
    {
        "type" => "integration_timeboard",
        "id" => 5
    },
    {
        "type" => "host_timeboard",
        "id" => 123456789
    }
]

result = dog.delete_items_from_dashboard_list(list_id, dashboards)

```

{{% /tab %}}
{{% tab "Curl" %}}

```sh

api_key=<DATADOG_API_KEY>
app_key=<DATADOG_APPLICATION_KEY>

list_id=4741

curl -X DELETE -H "Content-type: application/json" \
-d '{
        "dashboards": [
            {
                "type": "custom_screenboard",
                "id": 1414
            },
            {
                "type": "custom_timeboard",
                "id": 5858
            },
            {
                "type": "integration_screenboard",
                "id": 67
            },
            {
                "type": "integration_timeboard",
                "id": 5
            },
            {
                "type": "host_timeboard",
                "id": 123456789
            }
        ]
}' \
"https://api.datadoghq.com/api/v1/dashboard/lists/manual/${list_id}/dashboards?api_key=${api_key}&application_key=${app_key}"

```

{{% /tab %}}
{{< /tabs >}}

#### Example response

{{< tabs >}}
{{% tab "Python" %}}

```python
{
    'deleted_dashboards_from_list': [
        {
            'type': 'custom_timeboard',
            'id': 5858
        },
        {
            'type': 'custom_screenboard',
            'id': 1414
        },
        {
            'type': 'integration_timeboard',
            'id': 5
        },
        {
            'type': 'integration_screenboard',
            'id': 67
        },
        {
            'type': 'host_timeboard',
            'id': 123456789
        }
    ]
}

```

{{% /tab %}}
{{% tab "Ruby" %}}

```ruby
[
    "200",
    {
        "deleted_dashboards_from_list" => [
            {
                "type" => "custom_timeboard",
                "id" => 5858
            },
            {
                "type" => "custom_screenboard",
                "id" => 1414
            },
            {
                "type" => "integration_timeboard",
                "id" => 5
            },
            {
                "type" => "integration_screenboard",
                "id" => 67
            },
            {
                "type" => "host_timeboard",
                "id" => 123456789
            }
        ]
    }
]
```

{{% /tab %}}
{{% tab "Curl" %}}

```sh
{
    "deleted_dashboards_from_list": [
        {
            "type": "custom_timeboard",
            "id": 5858
        },
        {
            "type": "custom_screenboard",
            "id": 1414
        },
        {
            "type": "integration_timeboard",
            "id": 5
        },
        {
            "type": "integration_screenboard",
            "id": 67
        },
        {
            "type": "host_timeboard",
            "id": 123456789
        }
    ]
}
```

{{% /tab %}}
{{< /tabs >}}
