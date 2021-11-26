# commit-msg

replace `commit-msg.sample` script



e in `.git/hooks/ folder` or replace with your own script file with same name. :thumbsup:

```
#!/bin/sh

if ! head -1 "$1" | grep -qE "^(chore|docs|revert|refactor)(\(.+?\))?:? .{4,88}$"; then
    echo "Fail! Commit message is invalid. Follow the pattern 'NM-[0-9]{2,5}: message{4,88}" or "chore|revert|docs: message{4,88}'" >&2
    exit 1
fi
```

enable script with command `chmod +x <path/to/file>`

or use husky library and commit lint

```
yarn add husky -D
yarn commitlint @commitlint/cli -D
```

edit package.json

```
"scripts" : {
    "prepare": "husky install"
}
```

if .git and package.json are in [different folders](https://typicode.github.io/husky/#/?id=custom-directory): [example here](https://github.com/typicode/husky/issues/348)

```
"scripts" : {
    "prepare": "cd ../../folderwith.git && husky install path/tofolderwith/package.json
}
```

run prepare script:

```
yarn prepare
```

in the folder with package.json file new folder has been created -> `.husky`

add the `commit-msg` file in `.husky` folder: this script run the commit lint config

```
#!/bin/sh

cd path/tofolder/with.packagejson && yarn commitlint --edit $1
```

create a `commitlint-config.js` file

```
module.exports = {
  rules: {
    'type-enum': [0],
    'subject-case': [0],
    'jira-ticket': [2, 'always'],
  },
  plugins: [
    {
      rules: {
        'jira-ticket': (msg) => {
          if(/^(chore|revert|docs)(: )[a-z].+/.test(msg.header)) {
            return [true, 'No need a jira ticket with this type'];
          } else {
            if (/^NM-[\d]{4,5}(: )[a-z].+/.test(msg.header)) {
              return [true, 'Jira ticket id is present'];
            } else {
              return [false, 'No valid jira ticket id found. Use pattern "NM-[0-9]{4,5}: message" or "refactor|chore|revert|docs: message"'];
            }
          }
        },
      },
    }
  ],
};

```

to check how commilint works run:

```
echo "some commit message" | yarn commitlint
```

if hook is ignored [check this](https://stackoverflow.com/questions/8598639/why-is-my-git-pre-commit-hook-not-executable-by-default)
