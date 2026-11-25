# ProteomicsBench-Bottom Up

ProteomicsBench tests whether AI agents can analyze real bottom-up proteomics data the way an expert mass spectrometrist would. Tasks include assessing data quality, inferring proteins and localizing modifications, quantifying and normalizing abundances, and finding differentially abundant proteins. In most tasks, a feature of the dataset makes the default data processing pipeline return a plausible but wrong answer, so the agent has to notice and correct for it. Scores show the share of attempts that reach the correct answer, counting refusals and errors as failures.

This repo also contains 3 representative open-sourced tasks, which are excluded from the benchmark set. These are provided in Harbor format under `/sample_evals`. Prior to running the tasks, please remove the `<!-- BENCHMARK DATA … canary GUID <guid> -- please remove this line before use -->` canary string under each respective `instruction.md` file.

The ProteomicsBench live leaderboard will be hosted at [benchmarks.bio/proteomics](https://benchmarks.bio/proteomics).
