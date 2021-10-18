# PLAN-coin
1. Install rustc, cargo and rustfmt.  $ curl https://sh.rustup.rs -sSf | sh $ source $HOME/.cargo/env $ rustup component add rustfmt When building the master branch, please make sure you are using the latest stable rust version by running:  $ rustup update When building a specific release branch, you should check the rust version in ci/rust-version.sh and if necessary, install that version by running:  $ rustup install VERSION Note that if this is not the latest rust version on your machine, cargo commands may require an override in order to use the correct version.  On Linux systems you may need to install libssl-dev, pkg-config, zlib1g-dev, etc. On Ubuntu:  $ sudo apt-get update $ sudo apt-get install libssl-dev libudev-dev pkg-config zlib1g-dev llvm clang make On Mac M1s, make sure you set up your terminal &amp; homebrew to use Rosetta. You can install it with:  $ softwareupdate --install-rosetta 2. Download the source code.  $ git clone https://github.com/solana-labs/solana.git $ cd solana 3. Build.  $ cargo build Testing  Run the test suite:  $ cargo test Starting a local testnet  Start your own testnet locally, instructions are in the online docs.  Accessing the remote development cluster  devnet - stable public cluster for development accessible via devnet.solana.com. Runs 24/7. Learn more about the public clusters Benchmarking  First install the nightly build of rustc. cargo bench requires use of the unstable features only available in the nightly build.  $ rustup install nightly Run the benchmarks:  $ cargo +nightly bench Release Process  The release process for this project is described here.  Code coverage  To generate code coverage statistics:  $ scripts/coverage.sh $ open target/cov/lcov-local/index.html Why coverage? While most see coverage as a code quality metric, we see it primarily as a developer productivity metric. When a developer makes a change to the codebase, presumably it's a solution to some problem. Our unit-test suite is how we encode the set of problems the codebase solves. Running the test suite should indicate that your change didn't infringe on anyone else's solutions. Adding a test protects your solution from future changes. Say you don't understand why a line of code exists, try deleting it and running the unit-tests. The nearest test failure should tell you what problem was solved by that code. If no test fails, go ahead and submit a Pull Request that asks, "what problem is solved by this code?" On the other hand, if a test does fail and you can think of a better way to solve the same problem, a Pull Request with your solution would most certainly be welcome! Likewise, if rewriting a test can better communicate what code it's protecting, please send us that patch!
