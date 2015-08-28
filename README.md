# csv-to-protobuf

Encode csv to protobuf

	npm install csv-protobuf-stream

## Usage

``` js
var csvProtobuf = require('csv-protobuf-stream');
var split = require('binary-split');
var encoder = csvProtobuf();

fs.createReadStream('data.csv').pipe(split()).pipe(encoder).on('data', function(data) {
	console.log('protobuf row:', data);
	console.log('protobuf schema:', encoder.schema);
})
```

## Modify a on-demand schema

Before the schema is processed it is possible to intercept the schema specification to reduce the data-size:

```js
csvProtobuf(null, null, function schemaModifier(schema) {
    schema[0].type = 'int32'
})
```