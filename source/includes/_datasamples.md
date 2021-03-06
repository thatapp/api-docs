# Data samples

## Retrieve data sample
This resource allows you to retrieve data sample.

> Example Request:

```shell
 curl {{ api_base_url }}/v2/data-samples/{DATASAMPLE_ID} \
   -u {EMAIL}:{APIKEY} \
   -H 'Accept: application/json'
```

> Example Request with filter:

```shell
 curl {{ api_base_url }}/v2/data-samples?filter[id]={DATASAMPLE_ID1},{DATASAMPLE_ID2} \
   -u {EMAIL}:{APIKEY} \
   -H 'Accept: application/json'
```

> Example Response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "data":{
    "id":"{DATASAMPLE_ID}",
    "type":"data-sample",
    "links":{
      "self":"/v2/data-samples/585d389b90ea62ce348a478b"
    },
    "relationships":{
      "component_version":{
        "data":{
          "id":"latest",
          "type":"version"
        },
        "links":{
          "self":"/v2/components/5863f7136ef9da255ad9a9bc/versions/latest"
        }
      },
      "workspace":{
        "data":{
          "id":"59d341e9037f7200184a408b",
          "type":"workspace"
        },
        "links":{
          "self":"/v2/workspaces/59d341e9037f7200184a408b"
        }
      },
      "component":{
        "data":{
          "id":"5863f7136ef9da255ad9a9bc",
          "type":"component"
        },
        "links":{
          "self":"/v2/components/5863f7136ef9da255ad9a9bc"
        }
      },
      "user":{
        "data":{
          "id":"585d389b90ea62ce348a478b",
          "type":"user"
        },
        "links":{
          "self":"/v2/users/585d389b90ea62ce348a478b"
        }
      }
    },
    "attributes":{
      "method":"hello123",
      "result":{
        "foo":"bar1",
        "baz":"qwe1"
      }
    }
  },
  "meta":{}
}
```

### Authorization

A member of a Workspace can get any sample from own Workspace.

### HTTP Request

``GET {{ api_base_url }}/v2/data-samples/{DATASAMPLE_ID}``































## Create data sample

> Example Request:

```shell
 curl {{ api_base_url }}/v2/data-samples \
   -X POST \
   -u {EMAIL}:{APIKEY} \
   -H 'Accept: application/json' \
   -H 'Content-Type: application/json' -d '
   	{
  	"data":{
    	"type":"data-sample",
  	  "attributes":{
  	    "method":"hello123",
   	   "result":{
   	     "foo":"bar",
  	      "baz":"foo"
  	    }
  	  },
  	  "relationships":{
 	     "component":{
  	      "data":{
  	        "id":"5863f7136ef9da255ad9a9bc",
  	        "type":"component"
   	     }
    	  },
      	"component_version":{
     	   "data":{
     	     "id":"latest",
     	     "type":"version"
     	   }
     	 },
    	  "workspace":{
    	    "data":{
    	      "id":"59d341e9037f7200184a408b",
     	     "type":"workspace"
     	   }
   	   }
  	  }
 	 }
	}'
```

> Example Response:

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "data":{
    "id":"585d389b90ea62ce348a478b",
    "type":"data-sample",
    "links":{
      "self":"/v2/data-samples/585d389b90ea62ce348a478b"
    },
    "relationships":{
      "component_version":{
        "data":{
          "id":"latest",
          "type":"version"
        },
        "links":{
          "self":"/v2/components/5863f7136ef9da255ad9a9bc/versions/latest"
        }
      },
      "workspace":{
        "data":{
          "id":"59d341e9037f7200184a408b",
          "type":"workspace"
        },
        "links":{
          "self":"/v2/workspaces/59d341e9037f7200184a408b"
        }
      },
      "component":{
        "data":{
          "id":"5863f7136ef9da255ad9a9bc",
          "type":"component"
        },
        "links":{
          "self":"/v2/components/5863f7136ef9da255ad9a9bc"
        }
      },
      "user":{
        "data":{
          "id":"585d389b90ea62ce348a478b",
          "type":"user"
        },
        "links":{
          "self":"/v2/users/585d389b90ea62ce348a478b"
        }
      }
    },
    "attributes":{
      "method":"hello123",
      "result":{
        "foo":"bar1",
        "baz":"qwe1"
      }
    }
  },
  "meta":{}
}
```

### HTTP Request

``POST {{ api_base_url }}/v2/data-samples``


### Body Parameters

| Parameter | Required | Description |
| :--- | :--- | :--- |
| type | yes | A value must be ``data-sample`` |
| attributes.method | yes | Component's action or trigger name. |
| attributes.result | yes | Data sample body |
| relationships.component.data.id | yes | Component's id |
| relationships.component_version.data.id | yes | Revision of the component’s build. Use latest to retrieve the descriptor of the most recent successful build. |
| relationships.workspace.data.id | yes | An Id of the Wokspace |
| relationships.workspace.data.type | yes | A value must be ``workspace``  |

### Authorization
A member of a Workspace with permission `workspaces.flow.edit` can create a sample in own Workspace.




### Returns

Returns data sample object if the call succeeded.




## Update data sample

> Example Request:

```shell
 curl {{ api_base_url }}/v2/data-samples/{DATASAMPLE_ID} \
   -X PATCH \
   -u {EMAIL}:{APIKEY} \
   -H 'Accept: application/json' \
   -H 'Content-Type: application/json' -d '
   {
        "data": {
            "type": "data-sample",
            "attributes": {
                "method": "hello123",
                "result": {
                    "foo": "bar",
                    "baz": "foo"
                }
            }
        }
    }'
```

> Example Response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "data":{
    "id":"585d389b90ea62ce348a478b",
    "type":"data-sample",
    "links":{
      "self":"/v2/data-samples/585d389b90ea62ce348a478b"
    },
    "relationships":{
      "component_version":{
        "data":{
          "id":"latest",
          "type":"version"
        },
        "links":{
          "self":"/v2/components/5863f7136ef9da255ad9a9bc/versions/latest"
        }
      },
      "workspace":{
        "data":{
          "id":"59d341e9037f7200184a408b",
          "type":"workspace"
        },
        "links":{
          "self":"/v2/workspaces/59d341e9037f7200184a408b"
        }
      },
      "component":{
        "data":{
          "id":"5863f7136ef9da255ad9a9bc",
          "type":"component"
        },
        "links":{
          "self":"/v2/components/5863f7136ef9da255ad9a9bc"
        }
      },
      "user":{
        "data":{
          "id":"585d389b90ea62ce348a478b",
          "type":"user"
        },
        "links":{
          "self":"/v2/users/585d389b90ea62ce348a478b"
        }
      }
    },
    "attributes":{
      "method":"hello123",
      "result":{
        "foo":"bar",
        "baz":"foo"
      }
    }
  },
  "meta":{}
}
```

### HTTP Request

``PATCH {{ api_base_url }}/v2/data-samples/{DATASAMPLE_ID}``


### Body Parameters

| Parameter | Required | Description |
| :--- | :--- | :--- |
| type | yes | A value must be ``data-sample`` |
| attributes.result | no | Data sample body |

### Authorization
A member of a Workspace with permission `workspaces.flow.edit` can update a sample in own Workspace.



### Returns

Returns updated data sample object if the call succeeded.
