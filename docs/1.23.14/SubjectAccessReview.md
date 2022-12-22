# SubjectAccessReview

* [write operations](#write)

## write

  ### apis.authorization.k8s.io.v1.subjectaccessreviews.post

  create a SubjectAccessReview

  #### Query

  | Parameter | Description |
  | --------- | ----------- |
  | `qs` | Querystring object |
  | `qs.dryRun` | When present, indicates that modifications should not be persisted. An invalid or unrecognized dryRun directive will result in an error response and no further processing of the request. Valid values are: - All: all dry run stages will be processed |
  | `qs.fieldManager` | fieldManager is a name associated with the actor or entity that is making these changes. The value must be less than or 128 characters long, and only contain printable characters, as defined by https:&#x2F;&#x2F;golang.org&#x2F;pkg&#x2F;unicode&#x2F;#IsPrint. |
  | `qs.pretty` | If &#39;true&#39;, then the output is pretty printed. |

  #### Body

  | Parameter | Description |
  | --------- | ----------- |
  | `body` | #&#x2F;definitions&#x2F;io.k8s.api.authorization.v1.SubjectAccessReview |

