# Developer Team Recommendation for Bug Triaging

A Java experimental framework for bug triaging through expertise retrieval and developer-team recommendation. It connects bug reports, solver history, source-code evidence, and repository activity into a time-aware recommendation workflow.

## What the framework explores

The project models three developer groups—experienced developers, newcomers with repository evidence, and fresh graduates—and searches their expertise profiles for a bug's technical vocabulary. It also represents how accumulated bug-solving experience changes a developer's profile over time.

## Implementation pipeline

1. Parse bug reports and solver history into domain objects.
2. Collect repository information and extract source-code library imports.
3. Normalize terms using camel-case splitting, stop-word filtering, and stemming.
4. Build separate Lucene indexes for developer categories.
5. Query the indexes with bug keywords and combine candidate recommendations.
6. Update expertise records as the chronological experiment progresses and aggregate team results.

## Technical organization

`parser/` handles XML, source files, repository lists, and acquisition. `naturalLanguageProcessor/TextProcessor` prepares search terms. `profiles/` defines bugs and developer representations. `testing/Test` contains indexing, searches, category updates, and arithmetic/harmonic result aggregation; `testing/Result` stores experiment outcomes.

The `Test` constructor makes important experiment inputs explicit: team size, the solved-bug threshold for category transitions, the testing date, report/history files, and source/repository directories.

## Explore and run

Use a JDK supporting `java.net.http`, configure `src/` as the source root, and supply Apache Lucene, JavaParser, JGit, jsoup, JSON.simple, JDOM, and Snowball dependencies in the Java classpath. Provision the report files and repository directories referenced by `src/mainPackage/Main.java`; its configured workflow prepares repository evidence and constructs the experiment.

Begin with [Main.java](src/mainPackage/Main.java) for the experiment parameters and [Test.java](src/testing/Test.java) for recommendation and profile-update logic. `src/files/` holds the supporting text resources and output location.

## Technical contribution

The framework combines information retrieval with chronological expertise updates, making candidate categorization and team construction part of the same repository-informed bug-assignment experiment.
