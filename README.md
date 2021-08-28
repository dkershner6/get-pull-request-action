# get-pull-request-action

This action fetches a pull request based on simple inputs for use in non pull request triggers

## Usage

Simplest Possible Use (This works from an issue_comment trigger for a pull request):

```yml
      - uses: dkershner6/get-pull-request-action@v1
        id: get-pr
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          
      - run: echo ${{ fromJSON(steps.get-pr.outputs.pr).title }} # Make sure to use the fromJSON filter
```

Most Complicated Possible Use:

```yml
      - uses: dkershner6/get-pull-request-action@v1
        id: get-pr
        with:
          github-token: ${{ secrets.YOUR_PAT }} # PAT or similar required for cross-repo
          repo-owner: "someotherrepoowner"
          repo-name: "someotherreponame"
          pull-number: 7
          
      - run: echo ${{ fromJSON(steps.get-pr.outputs.pr).title }} # Make sure to use the fromJSON filter
```
