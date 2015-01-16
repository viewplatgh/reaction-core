## Product Schema

In Reaction Commerce, the product database model is designed to represent the business model in the most useful way possible. As such, the "product" object itself is just a wrapper and each variant within that product is the actual thing being purchased. This matches the business reality that shoppers aren't just purchasing a tshirt, they are purchasing a red tshirt or a blue tshirt.

To take this a step further, variant options are also complete "products" that happen to have a child-parent relationship to another variant. In the same way described above, when a shopper selects a tshirt design, a color, and then a size, they are actually buying a discrete "small red tshirt" product and not just a combinations of options.

Having a top level product with various attributes and values, as is common in other major ecommerce platforms (EAV model), only makes sense as a method to reconcile the realities of ecommerce data with a rigid relational database structure (SQL). Because Reaction uses a NoSQL document database (MongoDB), the data can be stored in a structure that is much more intelligible and in alignment with the actual business model.

Example of product data structure (as JSON):

```
{
  "_id" : "BCTMZ6HTxFSppJESk",
  "createdAt" : ISODate("2014-04-03T20:46:52.411Z"),
  "description" : "This is an example product.",
  "handle" : "example-product",
  "hashtags" : [
    "rpjCvTBGjhBi2xdro",
    "cseCBSSrJ3t8HQSNP"
  ],
  "isVisible" : true,
  "metafields" : [
    {
      "key" : "Material",
      "value" : "Cotton"
    },
    {
      "key" : "Quality",
      "value" : "Excellent"
    }
  ],
  "pageTitle" : "Basic Example Product",
  "productType" : "Simple",
  "shopId" : "WvrKDomkYth3THbDD",
  "title" : "Example Product",
  "updatedAt" : ISODate("2014-06-01T19:17:13.949Z"),
  "variants" : [
    {
      "_id" : "6qiqPwBkeJdtdQc4G",
      "title" : "Basic Example Variant",
      "price" : 19.99,
      "inventoryManagement" : true,
      "inventoryPolicy" : true,
      "updatedAt" : ISODate("2014-04-03T20:46:52.411Z"),
      "createdAt" : ISODate("2014-04-03T20:46:52.411Z"),
      "weight" : 35,
      "inventoryQuantity" : 49,
      "metafields" : [
        {
          "key" : null,
          "value" : null
        }
      ],
      "taxable" : false
    },
    {
      "_id" : "SMr4rhDFnYvFMtDTX",
      "title" : "Basic Example Variant",
      "price" : 19.99,
      "inventoryManagement" : true,
      "inventoryPolicy" : true,
      "updatedAt" : ISODate("2014-04-03T20:46:52.411Z"),
      "createdAt" : ISODate("2014-04-03T20:46:52.411Z"),
      "weight" : 35,
      "inventoryQuantity" : 45,
      "metafields" : [
        {
          "key" : null,
          "value" : null
        }
      ],
      "taxable" : false,
      "parentId" : "6qiqPwBkeJdtdQc4G",
      "optionTitle" : "Option 1"
    },
    {
      "_id" : "CJoRBm9vRrorc9mxZ",
      "title" : "Basic - Option 2",
      "price" : 12.99,
      "inventoryManagement" : true,
      "inventoryPolicy" : true,
      "updatedAt" : ISODate("2014-04-03T20:46:52.411Z"),
      "createdAt" : ISODate("2014-04-03T20:46:52.411Z"),
      "weight" : 35,
      "inventoryQuantity" : 42,
      "metafields" : [
        {
          "key" : null,
          "value" : null
        }
      ],
      "taxable" : false,
      "parentId" : "6qiqPwBkeJdtdQc4G",
      "optionTitle" : "Option 2"
    }
  ],
  "vendor" : "Example Manufacturer"
}
```
