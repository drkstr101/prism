# Prism Next

Experiments, demos, and tools for next-gen application development in Prism.

## Getting Started

Ensure that Java 17 or later is accessible on the system path. Then, run `./gradlew build` for local development and `./gradlew ci` for a complete release build (e.g., in GitHub Actions).

Look for any `.env.example` files and override any static global config values with a `.env` file, `.env.local` file, or system environment variable if needed.

## Contents

### [Gradle Plugin](prism-gradle/README.md)

Domain code used for building, validating, deploying, or other development tasks needed for this project.

### [Dev Stack](dev-stack/README.md)

- K3S Cluster
- Reverse Proxy
- Model Server

### [Prism UI](prism-ui/README.md)

## Getting Started
