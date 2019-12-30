# detect-pull-reqs
Detect pull requests between two branches.

- index.js
```javascript
const detect = require('detect-pull-reqs');

(async function main([ name, base, head ]) {
  const [ owner, repo ] = name.split('/');

  const pulls = await detect({
    token: process.env.GITHUB_TOKEN,
    owner,
    repo,
    base,
    head
  });
  console.log(pulls.map(p => p.html_url));

})(process.argv.slice(2)).catch(e => console.log(e));
```

```shell
$ node index.js grassedge/detect-pull-reqs production master
```