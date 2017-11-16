# JSON

## Python 2.7

```python
import json

def lambda_handler(event, context):
    
    data = {
        "result": 0 
    }
    data_string = json.dumps(data)
    data_json = json.loads(data_string)
    return data_json
```

```python
import json

def lambda_handler(event, context):
    data = {}
    data["result"] = 1
    data_string = json.dumps(data)
    data_json = json.loads(data_string)
    return data_json
```

