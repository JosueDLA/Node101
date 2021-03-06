# NPM Cheat Sheat

NPM is the default package manage system for Node.js

## Check version

```bash
> npm -v 
> node -v 
```

## Package.json
The init command creates a file called package.json after a few questions. This file contains all the information known about the project.

Initialize a new project

```bash
> npm init
```

Initialize a new project with default configuration

```bash
> npm init --yes
```

## Packages

NPM allows us to install, update and uninstall packages in a project. NPM also works as a repository for open-source packages created by the community.

Install a package

```bash
> npm install <package>
> npm i <package>
```

The installed package is listed automatically in the package.json file, under the dependencies list. If you are on a older version (<5) you have to manually specify it.

```bash
> npm i <package> --save
```

## Package dependencies

There are multiple types of dependencies, they are listed on the package.json file.

- __dependencies:__ these are the packages required by your application in production

- __devDependencies:__ packages that are only needed during development and testing

- __peerDependencies:__ these packages are only needed when publishing the package. when you include peerDependencies you define a specific version to be installed with your package. If this dependency exist it does nothing, if it does't exist or it is a different version it will show a warning.

- __optionalDependencies:__ these are optional dependencies, if they fail to install the installation process will continue.

- __bundleDependencies:__ is an array of packages that will be bundled with your package. This is useful when using a 3rd party package that is not available in NPM.

Install dependencies of a package.json

```bash
> npm i 
```

## Semantic Versioning

Semantic versioning (or SemVer for short) is a convention or standard when defining software version, depending on the nature of change that is being introduced.

- __Major:__ introduces a drastic change in the software. Usually not compatible with previous versions.

- __Minor:__ changes that add a new feature or modify an existing one, but it is still compatible with previous versions.

- __Patch:__ changes that fixes a bug and are backward compatible.

SemVer Structure

```
Major.Minor.Patch
```

### Tilde Ranges (~)

Allow patch-level changes if a minor version is specified on the comparator. Allow minor-level changes if not.

__~1.2.3:__ >=1.2.3 < 1.3.0
 
### Carret Ranges (^)

Allow changes that don't modify major versions.

__^1.2.3:__ >= 1.2.3 < 2.0.0

### Static Range

Only allows to install a certain version.

__1.2.3:__  == 1.2.3

## Working with packages

### Install / Uninstall a package

Install a specific verrsion of a package

```bash
> npm i <package>@<version>
```

Install a development package

```bash
> npm i <package>@<version>
```

Uninstall a package

```bash
> npm uninstall <package>
> npm un <package>
```

### List
NPM list shows all the installed packages and their dependencies version in a tree structure.

Show installed packages and dependencies

```bash
> npm list
```

Show only installed packages

```bash
> npm list --depth=0
```

### View

NPM view shows information about a certain package.

View package

```bash
> npm view <package>
```

View package dependencies

```bash
> npm view <package> dependencies
```

View all versions of a package

```bash
> npm view <package> versions
```

### Outdated

This command will check the registry to see if any installed packages are currently outdated.

```bash
> npm outdated
```

### Update

This command will update all the pacakes listed to the latest version, respecting SemVer.

```bash
> npm update
```

### Update with npm-check-update (ncu)

npm-check-updates upgrades your package.json dependencies to the latest version, ignoring SemVer.

Install npm-check-update globaly

```bash
> npm i -g npm-check-updates
```

Update package.json

```bash
> npm-check-updates -u
> ncu -u
```

Update packages

```bash
> npm i
```

## Publish a package

To publish a package you will need a NPM accout (you can register [here](https://www.npmjs.com/signup)), you can also register via terminal using the NPM CLI.

Register using NPM

 ```bash
> npm adduser
```

Login using NPM

```bash
> npm login
```

publish a package

```bash
> npm publish
```

## Update a published package

To update a published pacakge you will need to have a new software version, you can change the version of the software manually, or change it via NPM CLI.

New major version

```bash
> npm version major
```

New minor version

```bash
> npm version minor
```

New patch version

```bash
> npm version patch
```

Finaly you can update your package

```bash
> npm publish
```