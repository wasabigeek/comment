# Comment

[![Actions Status](https://github.com/jungwinter/comment/workflows/ci/badge.svg)](https://github.com/jungwinter/comment/actions)

> GitHub action to comment on PR, issue

## Inputs

- `type`: `create` or `edit`
- `body`: Comment body
- `token`: GitHub token
- `comment_id`: Comment id to edit body. Required with `edit` type.
- `issue_number`: Number of PR, issue to comment. Required with `create` type.

## Outputs

- `id`: Created or edited comment id
- `body`: comment body

## Example

```yaml
name: comment example
jobs:
  example:
    runs-on: ubuntu-latest
    steps:
      - name: Create comment
        uses: jungwinter/comment@v1
        id: create
        with:
          type: create
          body: "- [ ] Run tests"
          issue_number: '1'
          token: ${{ secrets.GITHUB_TOKEN }}

      - name: Update comment
        uses: jungwinter/comment@v1
        with:
          type: edit
          body: "- [x] Run tests"
          comment_id: ${{ steps.create.outputs.id }}
          token: ${{ secrets.GITHUB_TOKEN }}
```

---

[MIT license]


[MIT license]: LICENSE
