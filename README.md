# json-remap-keys
This script remaps keys in json files (jsonl format) using a mapping file, leveraging [jq](https://jqlang.org/). This mapping file should include "from" and "to" json keys in json path notation, combined with a ":" separator. This would look like the following example:

```
a.b:c.d.e
f.g:h
```

The script parses the mapping and leverages jq to parse each record and translate any found json key in the mapping. For example, using the above mapping, the following json:

```json
{"a":{"b":"value1"},"f":{"g":"other_value1"}}
{"a":{"b":"value2"},"f":{"g":"other_value2"}}
```

... would translate to:

```json
{"c":{"d":{"e":"value1"}},"h":"other_value1"}
{"c":{"d":{"e":"value2"}},"h":"other_value2"}
```



