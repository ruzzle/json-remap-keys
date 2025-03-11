# json-remap-keys
This self-contained script remaps keys in json files (jsonl format) using a mapping file, requiring/leveraging [jq](https://jqlang.org/).
The mapping file for the remapping should include "from" and "to" pairs, which both concern json keys in json path notation.
These pairs should be notated with a ":" separator. To visualize, this would look like the following:

```
a.b:c.d.e
f.g:h
```

The script parses the mapping and leverages jq to parse each record and translate any found json key in the mapping.For example, using the above mapping, the following json:

```json
{"a":{"b":"value1"},"f":{"g":"other_value1"}}
{"a":{"b":"value2"},"f":{"g":"other_value2"}}
```

... would translate to:

```json
{"c":{"d":{"e":"value1"}},"h":"other_value1"}
{"c":{"d":{"e":"value2"}},"h":"other_value2"}
```

## Usage
The script can be used as follos:

```
json-remap-keys <mapping-file> <json-file> # Supplying json file explicitly
json-remap-keys <mapping-file> # Reading from stdin
```
