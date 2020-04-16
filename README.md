Ever wanted to put JSON in a url? It's ugly, right?

To make it slightly better, you can use JSOUN (Javascript Object URL Notation).

## Example

```js
var JSOUN = require('./index.js')

var obj = {
    "glossary": {
        "title": "example glossary",
		"GlossDiv": {
            "title": "S",
			"GlossList": {
                "GlossEntry": {
                    "ID": "SGML",
					"SortAs": "SGML",
					"GlossTerm": "Standard Generalized Markup Language",
					"Acronym": "SGML",
					"Abbrev": "ISO 8879:1986",
					"GlossDef": {
                        "para": "A meta-markup language, used to create markup languages such as DocBook.",
						"GlossSeeAlso": ["GML", "XML"]
                    },
					"GlossSee": "markup"
                }
            }
        }
    }
}

var ugly = encodeURI(JSON.stringify(obj))
var pretty = JSOUN.encode(obj)

console.log(ugly)
console.log('\n\n')
console.log(pretty)
```

## Without JSOUN
```
%7B%22glossary%22:%7B%22title%22:%22example%20glossary%22,%22GlossDiv%22:%7B%22title%22:%22S%22,%22GlossList%22:%7B%22GlossEntry%22:%7B%22ID%22:%22SGML%22,%22SortAs%22:%22SGML%22,%22GlossTerm%22:%22Standard%20Generalized%20Markup%20Language%22,%22Acronym%22:%22SGML%22,%22Abbrev%22:%22ISO%208879:1986%22,%22GlossDef%22:%7B%22para%22:%22A%20meta-markup%20language,%20used%20to%20create%20markup%20languages%20such%20as%20DocBook.%22,%22GlossSeeAlso%22:%5B%22GML%22,%22XML%22%5D%7D,%22GlossSee%22:%22markup%22%7D%7D%7D%7D%7D
```

## With JSOUN
```
('glossary':('title':'example_glossary','GlossDiv':('title':'S','GlossList':('GlossEntry':('ID':'SGML','SortAs':'SGML','GlossTerm':'Standard_Generalized_Markup_Language','Acronym':'SGML','Abbrev':'ISO_8879:1986','GlossDef':('para':'A_meta-markup_language,_used_to_create_markup_languages_such_as_DocBook.','GlossSeeAlso':~'GML','XML';),'GlossSee':'markup')))))
```

## Note

JSOUN is only 100% safe in the fragment part of the url, i.e. after the # delimiter.