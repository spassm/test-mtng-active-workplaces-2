* SDLC
  * Codebase Management
    * For early phase project we can keep mono-repo approach, later - I would prefer to split it to different GIT-repos (governance and exclude unauthorized cross-changes)
    * maybe GIT-modules will be useful for team artifacts version control (git-commit pin per module to exclude broken CI when plans/priority are different for product teams)

  * Rework repo structure - introduce highlevel directories per product stream team - right now root directory contains dirs mix for different system components (frontend, backend, Solidity-contracts)
    * e.g. 'src' move to 'frontend/webapp', 'server' to 'backend', 'test, contracts' to 'web3'
    * add 'test' directories for each projects and try to introduce TDD practice

  * Team guides
    * Create Dev guides with best practice and high level approaches per each tech-stack or product stream team
    * Create Onboarding QA/Dev guides for env setup, access request flow and etc
    * Create sharable guides for setup/usage of development tools (e.g. charles proxy / burp suite, Metamask and etc)

  * DevOps(Sec) practices/approaches
    * Cleanup code - remove all hardcoded values (e.g. urls), use some kind of single config file to declare all env vars (with default values for local dev env)
      * Make agreement between devs and devops how to each team will manage new env-related vars for remote envs (config file from git-repo can be replaced in CD-pipeline)
    * Setup separate CI/CD pipelines per product stream team
      * need to establish CI-pipeline artifact versioning, that only verified and signed versions could be deployed to remote envs/app stores and than replace git-commit pin
      * need to add CI-pipeline stage to check critical vulnerabilities in dependencies
      * need to setup Dependabot or something like that to check dependency versions updates
    * Try to switch to API First approach based on OpenAPI v3
      * routes generator can reduce boiler plates in code
      * adding possibility include additional CI-pipeline stages like Fitness Functions (security check, REST-url correctness and etc), Contract Testing (Consumer-Driven)

* ETH/Web3
  * Local development
    * Run ETH-client (like geth) locally is too expensive for newcomers onboarding and CI-pipelines
    * Web3-product team should prepare snapshots of test-networks to decrease sync time or maintain centralized testnet geth-node for all teammembers
    * Also, Web3-team need to have faucets management to share testnet tokens for any teammates (devs, QAs and etc) - sharable creds in 1Password for example