# Eventの値の処理

## Python 2.7

```python
def lambda_handler(event, context):
    try:
        name=event["name"]
        print(name)
        return 1
    except Exception, e:
        print e, 'error'
        return -1
```

