---
name: npm-cli
description: 'Reference and index of documentation pages for npm CLI commands and configurations. You MUST load this skill when interacting with the npm CLI or asking about npm configuration, package.json, or npm scripts.'
license: MIT
---
# Skill: npm-cli

<!-- markdownlint-disable MD013 MD023 MD031 MD032 -->

## When to Use

- When needing documentation or usage instructions for specific `npm` commands (e.g., `npm install`, `npm exec`, `npm ci`).
- When dealing with npm configuration files like `.npmrc`, `package.json`, or `package-lock.json`.
- When understanding npm concepts such as workspaces, scopes, and dependency selectors.

## When Not to Use

- When managing alternative package managers like `yarn` or `pnpm`.
- When writing general JavaScript/TypeScript code that does not interact with npm packages or scripts.

## References

The following pages are mapped from the official npm documentation (v11.15.0). Use webfetch to read the raw markdown contents for deep insights into each command and concept.
To fully utilize this skill, you MUST read at least one of the links relevant to the current context:

### CLI Commands

- **npm**: [javascript package manager](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm.md)
- **npm access**: [Set access level on published packages](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-access.md)
- **npm adduser**: [Add a registry user account](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-adduser.md)
- **npm audit**: [Run a security audit](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-audit.md)
- **npm bugs**: [Report bugs for a package in a web browser](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-bugs.md)
- **npm cache**: [Manipulates packages cache](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-cache.md)
- **npm ci**: [Clean install a project](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-ci.md)
- **npm completion**: [Tab Completion for npm](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-completion.md)
- **npm config**: [Manage the npm configuration files](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-config.md)
- **npm dedupe**: [Reduce duplication in the package tree](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-dedupe.md)
- **npm deprecate**: [Deprecate a version of a package](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-deprecate.md)
- **npm diff**: [The registry diff command](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-diff.md)
- **npm dist-tag**: [Modify package distribution tags](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-dist-tag.md)
- **npm docs**: [Open documentation for a package in a web browser](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-docs.md)
- **npm doctor**: [Check the health of your npm environment](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-doctor.md)
- **npm edit**: [Edit an installed package](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-edit.md)
- **npm exec**: [Run a command from a local or remote npm package](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-exec.md)
- **npm explain**: [Explain installed packages](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-explain.md)
- **npm explore**: [Browse an installed package](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-explore.md)
- **npm find-dupes**: [Find duplication in the package tree](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-find-dupes.md)
- **npm fund**: [Retrieve funding information](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-fund.md)
- **npm get**: [Get a value from the npm configuration](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-get.md)
- **npm help**: [Get help on npm](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-help.md)
- **npm help-search**: [Search npm help documentation](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-help-search.md)
- **npm init**: [Create a package.json file](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-init.md)
- **npm install**: [Install a package](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-install.md)
- **npm install-ci-test**: [Install a project with a clean slate and run tests](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-install-ci-test.md)
- **npm install-test**: [Install package(s) and run tests](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-install-test.md)
- **npm link**: [Symlink a package folder](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-link.md)
- **npm ll**: [List installed packages](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-ll.md)
- **npm login**: [Login to a registry user account](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-login.md)
- **npm logout**: [Log out of the registry](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-logout.md)
- **npm ls**: [List installed packages](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-ls.md)
- **npm org**: [Manage orgs](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-org.md)
- **npm outdated**: [Check for outdated packages](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-outdated.md)
- **npm owner**: [Manage package owners](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-owner.md)
- **npm pack**: [Create a tarball from a package](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-pack.md)
- **npm ping**: [Ping npm registry](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-ping.md)
- **npm pkg**: [Manages your package.json](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-pkg.md)
- **npm prefix**: [Display prefix](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-prefix.md)
- **npm profile**: [Change settings on your registry profile](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-profile.md)
- **npm prune**: [Remove extraneous packages](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-prune.md)
- **npm publish**: [Publish a package](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-publish.md)
- **npm query**: [Dependency selector query](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-query.md)
- **npm rebuild**: [Rebuild a package](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-rebuild.md)
- **npm repo**: [Open package repository page in the browser](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-repo.md)
- **npm restart**: [Restart a package](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-restart.md)
- **npm root**: [Display npm root](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-root.md)
- **npm run**: [Run arbitrary package scripts](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-run.md)
- **npm sbom**: [Generate a Software Bill of Materials (SBOM)](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-sbom.md)
- **npm search**: [Search for packages](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-search.md)
- **npm set**: [Set a value in the npm configuration](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-set.md)
- **npm shrinkwrap**: [Lock down dependency versions for publication](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-shrinkwrap.md)
- **npm stage**: [Stage packages for publishing](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-stage.md)
- **npm star**: [Mark your favorite packages](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-star.md)
- **npm stars**: [View packages marked as favorites](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-stars.md)
- **npm start**: [Start a package](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-start.md)
- **npm stop**: [Stop a package](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-stop.md)
- **npm team**: [Manage organization teams and team memberships](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-team.md)
- **npm test**: [Test a package](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-test.md)
- **npm token**: [Manage your authentication tokens](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-token.md)
- **npm trust**: [Manage trusted publishing relationships between packages and CI/CD providers](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-trust.md)
- **npm undeprecate**: [Undeprecate a version of a package](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-undeprecate.md)
- **npm uninstall**: [Remove a package](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-uninstall.md)
- **npm unpublish**: [Remove a package from the registry](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-unpublish.md)
- **npm unstar**: [Remove an item from your favorite packages](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-unstar.md)
- **npm update**: [Update packages](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-update.md)
- **npm version**: [Bump a package version](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-version.md)
- **npm view**: [View registry info](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-view.md)
- **npm whoami**: [Display npm username](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npm-whoami.md)
- **npx**: [Run a command from a local or remote npm package](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/commands/npx.md)

### Configuring npm

- **Install**: [Download and install node and npm](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/configuring-npm/install.md)
- **Folders**: [Folder structures used by npm](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/configuring-npm/folders.md)
- **.npmrc**: [The npm config files](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/configuring-npm/npmrc.md)
- **npm-shrinkwrap.json**: [A publishable lockfile](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/configuring-npm/npm-shrinkwrap-json.md)
- **package.json**: [Specifics of npm's package.json handling](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/configuring-npm/package-json.md)
- **package-lock.json**: [A manifestation of the manifest](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/configuring-npm/package-lock-json.md)

### Using npm

- **Registry**: [The JavaScript Package Registry](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/using-npm/registry.md)
- **Package spec**: [Package name specifier](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/using-npm/package-spec.md)
- **Config**: [About npm configuration](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/using-npm/config.md)
- **Logging**: [Why, What & How we Log](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/using-npm/logging.md)
- **Scope**: [Scoped packages](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/using-npm/scope.md)
- **Scripts**: [How npm handles the "scripts" field](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/using-npm/scripts.md)
- **Workspaces**: [Working with workspaces](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/using-npm/workspaces.md)
- **Organizations**: [Working with teams & organizations](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/using-npm/orgs.md)
- **Dependency Selectors**: [Dependency Selector Syntax & Querying](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/using-npm/dependency-selectors.md)
- **Developers**: [Developer guide](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/using-npm/developers.md)
- **Removal**: [Cleaning the slate](https://raw.githubusercontent.com/npm/cli/refs/tags/v11.15.0/docs/lib/content/using-npm/removal.md)
