# ProteomicsBench-Bottom Up

Tests whether AI agents can analyze real bottom-up proteomics data the way an expert mass spectrometrist would. Tasks include assessing data quality, inferring proteins and localizing modifications, quantifying and normalizing abundances, and finding differentially abundant proteins. In most tasks, a feature of the dataset makes the default data processing pipeline return a plausible but wrong answer, so the agent has to notice and correct for it. Scores show the share of attempts that reach the correct answer, counting refusals and errors as failures.

This repo also contains 3 open-sourced tasks, which are provided in Harbor format. 
