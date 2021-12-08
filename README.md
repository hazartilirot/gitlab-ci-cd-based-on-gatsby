Some notes relating to .gitlab.ci.yml

- if the image is specified at the top it'll be by default used in each stage 
wherein is no image
- default Gatsby ports: 9000 in serve, 8000 in develop
- gatsby serve & - an ampersand runs the process in the background
- | tac | tac | - is a workaround for an error: (23) Failed writing body 
  https://stackoverflow.com/a/28879552/1521866
- Before deploying a project on Surge, type in a console `surge TOKEN`. Then 
  go to `https://gitlab.com/<username>/<project>/-/settings/ci_cd` and 
  create two new environment variables:

`Project name -> CI/CD -> Variables -> Add variable`

`SURGE_LOGIN` - email used in the middle of the registration process

`SURGE_TOKEN` - token provided by the above command

`$CI_COMMIT_SHORT_SHA` is predefined variable, it'll return the first eight 
characters of CI_COMMIT_SHA [Docs](https://docs.gitlab.com/ee/ci/variables/predefined_variables.html#predefined-variables-reference)

`sed -i "s/%%VERSION%%/$CI_COMMIT_SHORT_SHA" ./public/index.html` - sed is a 
linux command replacing a placeholder (or a marker like %%VERSION%% is 
placed in index.js file) with a specified key word, in our case it's an 
environment variable.