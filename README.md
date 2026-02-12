## Project Setup

### 1. Setup your ssh key in Bitbucket Support

Navigate to [SSH Keys](https://bitbucket.org/account/settings/) and hit `SSH keys` button. Your SSH key, if you created one, can be found
in `~/.ssh/id_rsa.pub`

#### Generate the SSH Key

Run `ssh-keygen`

[Bitbucket Documentation](https://support.atlassian.com/bitbucket-cloud/docs/set-up-an-ssh-key/?permissionViolation=true)

### 2. Clone project locally

Run `git clone <repo-url>`

```bash
git clone git@bitbucket.org:network-international/qa-automation-framework-poc.git
cd .qa-automation-framework-poc
```

## Local development

One of the following can be used for the build:

- build with tests

```bash
  mvn clean install
```

- build without tests

```bash
  mvn clean install -DskipTests=true
```

- if you want to run the Regression suite on DEV environment'

```bash
mvn clean install -Denvironment=DEV -Dit.test=RegressionTestSuite verify
mvn clean install -DargLine="-Dspring.profiles.active=qa" verify
```

## NI Git Flow

- `master` — All development code is merged into `master`
  ​ During the development cycle, a variety of supporting branches are used:
  ​
- `feature/[Story Number] `— feature branches are used to develop new features for the upcoming releases. May branch off from `master` and must merge
  into `master`.
- `release/[YYYY-MM-DD]` — release branches support preparation of a new production release. They allow many minor bug to be fixed and preparation of
  meta-data for a release. May branch off from master and must be merged in master after release tag was created.
- `bugfix/[Bug Number]` — bugfix branches are necessary to act immediately upon an undesired status of specific `release/*` branch. May branch off
  from specific `release/*` branch and must merge into the same `release/*` branch and `master` if it's required.

mvn clean install -Ddriver=chrome -DEnvironment=DEV -Dcucumber.options="--tags @RegressionUi"