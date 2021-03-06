# @json

## `@json` section defines HTTP routes that return `application/json` content.

`@json` routes:

- Must be either an HTTP `POST` or `GET`
- Can have Express-style URL parameters

This `.arc` file defines some typical JSON routes:

```arc
@app
testapp

@json
get /notes          
get /notes/:noteID
post /notes                # create a note
post /notes/:noteID        # update a note
post /notes/:noteID/delete # delete a note
```

The `.arc` above generates the following REST-ish functions:

```bash
/
|-- html
|   |-- get-notes/
|   |-- get-notes-000noteID/
|   |-- post-notes/
|   |-- post-notes-000noteID/
|   `-- post-notes-000noteID-delete/
|-- .arc
`-- package.json
```

Note: The route `/notes/:noteID` corresponding handler deliberately looks a bit weird with the triple `000` so you can quickly identify URL params from URL parts. The Lambda deploy targets follow suit:

- `testapp-staging-get-notes-000noteID`
- `testapp-production-get-notes-000noteID`

## Next: [Defining events with `@events`](/reference/events)
