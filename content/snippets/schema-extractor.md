---
title: Schema Extractor
---
将 JSON/YAML 的结构提取出来

```python
#!/usr/bin/env python3

import json
import sys

import yaml

def extract_schema(obj):
    if isinstance(obj, dict):
        return {k: extract_schema(v) for k, v in obj.items()}
    if isinstance(obj, list):
        return [f'list[{len(obj)}]', extract_schema(obj[0]) if obj else None]
    return type(obj).__name__

def main():
    content = ''
    try:
        while True:
            line = input()
            content += line + '\n'
    except EOFError:
        pass

    try:
        obj = yaml.safe_load(content)
    except yaml.YAMLError:
        print('fatal: input is neither valid JSON nor YAML', file=sys.stderr)
        exit(1)

    schema = extract_schema(obj)
    print(json.dumps(schema, indent=2))

if __name__ == '__main__':
    main()
```