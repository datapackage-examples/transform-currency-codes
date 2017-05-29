This is an example Data Package to demonstrate how data transforms works. In this example, we explain how getting a sample from a dataset can be done before data package gets rendered in showcase page. It assumes publisher is already familiar with Data Packages and views specifications (`views` property in Data Package specifications).

### Getting sample data

On the top of this page, you can find a table that displays filtered data. Raw data is displayed in preview section. As you can see we are getting sample of 15 rows from the initial data. This is described in the second view object of `views` property:

* `"specType": "table"` - this way we define the view as a table (other options are `"simple"` (renders a graph and accepts Plotly spec) and `"vega"` (renders a graph and accepts Vega spec)).
* `"resources"` property is an array of objects in this case, where publishers can define data transforms they want to apply.
* `"name"` - name of the resource as a reference.
* `"transform"` - array of transforms. Each transform is an object, which properties vary depending on transform type. Only common property is `"type"` that is used to specify transform type.

Transform properties for "sample":

* `"type": "sample"` - this way we define the transform to be a sample.
* `"size"` - any integer that will be used as a size of a sample data.

{{ dp.json }}
