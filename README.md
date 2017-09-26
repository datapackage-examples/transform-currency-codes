This is an example dataset to demonstrate how data transforms works. In this example, we explain how to get a sample from a resource. We assume a publisher is already familiar with Data Packages and views specifications (`views` property in Data Package specifications).

### Getting sample data

On the top of this page, you can find a table that displays filtered data. Raw data is displayed in preview section. As you can see we are getting sample of 15 rows from the initial data. This is described in the view object of `views` property:

```
{
  "name": "sample-view",
  "specType": "table",
  "resources": [
    {
      "name": "codes-all",
      "transform": [
        {
          "type": "sample",
          "size": 15
        }
      ]
    }
  ]
}
```

where:

* `"specType": "table"` - this way we define the view as a table (other options are `"simple"` (renders a graph and accepts Plotly spec) and `"vega"` (renders a graph and accepts Vega spec)).
* `"resources"` property is an array of objects in this case, where publishers can define data transforms they want to apply.
* `"name"` - name of the resource as a reference.
* `"transform"` - array of transforms. Each transform is an object, which properties vary depending on transform type. Only common property is `"type"` that is used to specify transform type.

Transform properties for "sample":

* `"type": "sample"` - this way we define the transform to be a sample.
* `"size"` - any integer that will be used as a size of a sample data.

### Descriptor for this data package

This is the full `datapackage.json` of this dataset:

```
{
  "name": "example-sample-transform-on-currency-codes",
  "title": "Example sample transform on ISO 4217 Currency Codes",
  "licenses": [
    {
      "id": "odc-pddl",
      "label": "Open Data Commons Public Domain Dedication and Licence (PDDL)",
      "url": "http://opendatacommons.org/licenses/pddl/"
    }
  ],
  "keywords": [ "iso", "iso-4217", "currency", "codes" ],
  "homepage": "http://www.iso.org/iso/currency_codes",
  "sources": [{
    "name": "SIX Interbank Clearing Ltd (on behalf of ISO)",
    "email": "office@currency-iso.org"
  }],
  "maintainer": [{
    "name": "Rufus Pollock",
    "email": "rufus.pollock@okfn.org"
  }],
  "contributors": [
    {
      "name": "Rufus Pollock",
      "email": "rufus.pollock@okfn.org"
    },
    {
      "name": "Kristofer D. Kusano",
      "email": "kdkusano@gmail.com"
    }
  ],
  "resources": [
    {
      "name": "codes-all",
      "path": "data/codes-all.csv",
      "mimetype": "text/csv",
      "size": "16863",
      "schema": {
        "fields": [
          {
            "name": "Entity",
            "type": "string",
            "description": "Country or region name"
          },
          {
            "name": "Currency",
            "type": "string",
            "description": "Name of the currency"
          },
          {
            "name": "AlphabeticCode",
            "title": "Alphabetic Code",
            "type": "string",
            "description": "3 digit alphabetic code for the currency"
          },
          {
            "name": "NumericCode",
            "title": "Numeric Code",
            "type": "integer",
            "description": "3 digit numeric code"
          },
          {
            "name": "MinorUnit",
            "title": "Minor Unit",
            "type": "number",
            "description": ""
          },
          {
            "name": "WithdrawalDate",
            "title": "Withdrawal Date",
            "type": "string",
            "description": "Date currency withdrawn (values can be ranges or months"
          }
        ]
      }
    }
  ],
  "views": [
    {
      "name": "sample-view",
      "specType": "table",
      "resources": [
        {
          "name": "codes-all",
          "transform": [
            {
              "type": "sample",
              "size": 15
            }
          ]
        }
      ]
    }
  ]
}
```
