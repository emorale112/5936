---
tags: [Custom Fields]
---

# Getting Custom Fields

## Instructions

There are a few ways to get custom fields from the Gusto API. First, if you only need the custom field schema for a company and not the values for any individual, you can go to [Get the custom fields of a company](https://gusto.stoplight.io/docs/api/reference/Gusto-API.v1.yaml/paths/~1v1~1companies~1%7Bcompany_id%7D~1custom_fields/get).

If you want the custom fields, including responses, for one particular individual, then you can go to [Get an employee's custom fields](https://gusto.stoplight.io/docs/api/reference/Gusto-API.v1.yaml/paths/~1v1~1employees~1%7Bemployee_id%7D~1custom_fields/get). Another option is to fetch that data when you make a get request for a [single employee](https://gusto.stoplight.io/docs/api/reference/Gusto-API.v1.yaml/paths/~1v1~1employees~1%7Bemployee_id%7D/get) by passing in include=custom_fields in the params.

Finally, to get all the custom fields, including responses, for all employees, we recommend that you pass in include=custom_fields in the params when you all employees from the [employees endpoint](https://gusto.stoplight.io/docs/api/reference/Gusto-API.v1.yaml/paths/~1v1~1companies~1%7Bcompany_id%7D~1employees/get).

## Caveats

When you fetch the company custom fields, you are guaranteed to get all the custom fields that exist for that company. When you fetch it for an individual/invidiuals (for example, if you want the responses as well), only custom fields that have been filled out with values by the user will appear. So the return value could be an array from size 0 to number of custom fields present, depending on how many fields have been filled out by the user.

Additionally, another possible zero state is that the user could have filled out a value for the custom field and then later replaced it with a blank value. Our API would return that custom field, but with the value as a blank string. That is a limitation of our API and how we handle custom fields, as there is no way to "delete" a custom field response presently. But it probably is something you should be aware of.

For example, let's say you have a company with three custom fields. When you query the company custom fields endpoint you will get a schema that looks like this:
```json
{
  "custom_fields": [
    {
      "id": "ea7e5d57-6abb-47d7-b654-347c142886c0",
      "name": "employee_level",
      "description": "Employee Level",
      "type": "text",
      "selection_options": null
    },
    {
      "id": "299650e4-e970-4acf-9bf0-6f05585d20ba",
      "name": "t-shirt size",
      "description": "What is your t-shirt size?",
      "type": "text",
      "selection_options": null
    },
    {
      "id": "024ec137-6c92-43a3-b061-14a9720531d6",
      "name": "favorite fruit",
      "description": "Which is your favorite fruit?",
      "type": "text",
      "selection_options": null
    }
  ]
}
```

Now imagine you get the custom fields for an individual who:
1. Has never filled out the employee level custom field
2. Has filled out the t-shirt size field but then replaced it with a blank
3. Has filled out the fruit question with their favorite fruit

The response would look something like this:
```json
{
  "custom_fields": [
    {
      "id": "3796e08d-c2e3-434c-b4de-4ce1893e7b59",
      "company_custom_field_id": "299650e4-e970-4acf-9bf0-6f05585d20ba",
      "name": "t-shirt size",
      "description": "What is your t-shirt size?",
      "type": "text",
      "value": "",
      "selection_options": null
    },
    {
      "id": "3796e08d-c2e3-434c-b4de-4ce1893e7b59",
      "company_custom_field_id": "024ec137-6c92-43a3-b061-14a9720531d6",
      "name": "favorite fruit",
      "description": "Which is your favorite fruit?",
      "type": "text",
      "value": "apple",
      "selection_options": null
    }
  ]
}
```

Note the edge cases of #1 and #2.
