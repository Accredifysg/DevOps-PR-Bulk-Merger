# Bulk merger

Bulk merge Pull Requests. This repo is forked from https://github.com/alphagov/bulk-merger.

View original README on https://github.com/alphagov/bulk-merger/blob/main/README.md

## Setup

### GitHub Token Setup

Create a "Personal access token", with at least the `repo/public_repo`
scope. Add your token with repo access to `.env`:

```
export GITHUB_TOKEN=<yourtoken>
```

The scripts will use this token to talk to GitHub.

### Ruby setup

Install Ruby using [asdf](https://github.com/asdf-vm/asdf). This project is using Ruby 3.3.6 (from .ruby-version).

```
asdf plugin add ruby
asdf install ruby 3.3.6
asdf global ruby 3.3.6
```

After that, install the dependency of this project. If you dont have budler yet, install it with `gem install bundler`. `gem` should be installed already when you install ruby via asdf.
```
bundle install
```

## Bulk approve PRs

```
./review 'bump hashicorp/aws'
```

This looks for unreviewed PRs in `accredifysg` with "bump hashicorp/aws" in the title. If it finds any, it will list them out and ask you to confirm if you want to approve them.


```shell
❯ ./review "bump hashicorp/aws"
Searching for PRs containing 'bump hashicorp/aws'
Found 8 unreviewed PRs:

- 'Bump hashicorp/aws from 5.96.0 to 5.98.0' (https://github.com/Accredifysg/Accredify-Infra/pull/303) 
- 'Bump hashicorp/aws from 5.95.0 to 5.98.0' (https://github.com/Accredifysg/Accredify-Main-Infra/pull/72) 
- 'Bump hashicorp/aws from 5.96.0 to 5.98.0' (https://github.com/Accredifysg/Analytics-Infra/pull/76) 
- 'chore(deps): bump hashicorp/aws from 5.97.0 to 5.98.0' (https://github.com/Accredifysg/Audit-Infra/pull/39) 
- 'Bump hashicorp/aws from 5.96.0 to 5.98.0' (https://github.com/Accredifysg/Log-Archive-Infra/pull/87) 
- 'Bump hashicorp/aws from 5.97.0 to 5.98.0' (https://github.com/Accredifysg/Monitoring-Infra/pull/71) 
- 'Bump hashicorp/aws from 5.97.0 to 5.98.0' (https://github.com/Accredifysg/Nexus-Whitelabel-Infra/pull/109) 
- 'Bump hashicorp/aws from 5.97.0 to 5.98.0' (https://github.com/Accredifysg/P3-Spike-Infra/pull/122) 

Have you reviewed the changes, and you want to approve all these PRs? [y/N]
y
OK! 👍 Approving away...
Reviewing PR 'Bump hashicorp/aws from 5.96.0 to 5.98.0' (https://github.com/Accredifysg/Accredify-Infra/pull/303) ✅
Reviewing PR 'Bump hashicorp/aws from 5.95.0 to 5.98.0' (https://github.com/Accredifysg/Accredify-Main-Infra/pull/72) ✅
Reviewing PR 'Bump hashicorp/aws from 5.96.0 to 5.98.0' (https://github.com/Accredifysg/Analytics-Infra/pull/76) ✅
Reviewing PR 'chore(deps): bump hashicorp/aws from 5.97.0 to 5.98.0' (https://github.com/Accredifysg/Audit-Infra/pull/39) ✅
Reviewing PR 'Bump hashicorp/aws from 5.96.0 to 5.98.0' (https://github.com/Accredifysg/Log-Archive-Infra/pull/87) ✅
Reviewing PR 'Bump hashicorp/aws from 5.97.0 to 5.98.0' (https://github.com/Accredifysg/Monitoring-Infra/pull/71) ✅
Reviewing PR 'Bump hashicorp/aws from 5.97.0 to 5.98.0' (https://github.com/Accredifysg/Nexus-Whitelabel-Infra/pull/109) ✅
Reviewing PR 'Bump hashicorp/aws from 5.97.0 to 5.98.0' (https://github.com/Accredifysg/P3-Spike-Infra/pull/122) ✅
```

## Approve & merge all Pull Requests

```
./merge "bump hashicorp/aws"
```

This will run the `./review` script above, and also merge the approved PRs. I added a 10 second delay between merges to throttle merge process. There could be multiple dependabot PRs within one project, and it need time to sync between main branches and.


```sh
Proceed with caution. If you are unsure about any part of this process, consult with your team.
Searching for PRs containing 'bump hashicorp/aws'
No unreviewed PRs found!
Found 7 reviewed but unmerged PRs:

- Accredifysg/Accredify-Infra 'Bump hashicorp/aws from 5.96.0 to 5.98.0' (https://github.com/Accredifysg/Accredify-Infra/pull/303) 
- Accredifysg/Analytics-Infra 'Bump hashicorp/aws from 5.96.0 to 5.98.0' (https://github.com/Accredifysg/Analytics-Infra/pull/76) 
- Accredifysg/Audit-Infra 'chore(deps): bump hashicorp/aws from 5.97.0 to 5.98.0' (https://github.com/Accredifysg/Audit-Infra/pull/39) 
- Accredifysg/Log-Archive-Infra 'Bump hashicorp/aws from 5.96.0 to 5.98.0' (https://github.com/Accredifysg/Log-Archive-Infra/pull/87) 
- Accredifysg/Monitoring-Infra 'Bump hashicorp/aws from 5.97.0 to 5.98.0' (https://github.com/Accredifysg/Monitoring-Infra/pull/71) 
- Accredifysg/Nexus-Whitelabel-Infra 'Bump hashicorp/aws from 5.97.0 to 5.98.0' (https://github.com/Accredifysg/Nexus-Whitelabel-Infra/pull/109) 
- Accredifysg/P3-Spike-Infra 'Bump hashicorp/aws from 5.97.0 to 5.98.0' (https://github.com/Accredifysg/P3-Spike-Infra/pull/122) 

Have you reviewed the changes, and you want to MERGE all these PRs? [y/N]
y
OK! 👍 Merging away...
Merging PR 'Bump hashicorp/aws from 5.96.0 to 5.98.0' (https://github.com/Accredifysg/Accredify-Infra/pull/303) ✅
Merging PR 'Bump hashicorp/aws from 5.96.0 to 5.98.0' (https://github.com/Accredifysg/Analytics-Infra/pull/76) ✅
Merging PR 'chore(deps): bump hashicorp/aws from 5.97.0 to 5.98.0' (https://github.com/Accredifysg/Audit-Infra/pull/39) ✅
Merging PR 'Bump hashicorp/aws from 5.96.0 to 5.98.0' (https://github.com/Accredifysg/Log-Archive-Infra/pull/87) ✅
Merging PR 'Bump hashicorp/aws from 5.97.0 to 5.98.0' (https://github.com/Accredifysg/Monitoring-Infra/pull/71) ✅
Merging PR 'Bump hashicorp/aws from 5.97.0 to 5.98.0' (https://github.com/Accredifysg/Nexus-Whitelabel-Infra/pull/109) ✅
Merging PR 'Bump hashicorp/aws from 5.97.0 to 5.98.0' (https://github.com/Accredifysg/P3-Spike-Infra/pull/122) ✅
```

## Licence

[MIT License](LICENCE)
