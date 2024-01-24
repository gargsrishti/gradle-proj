# Gradle Version Catalog and Dependency Locking Issue

## Overview

This small Gradle project is created to reproduce a specific issue related to version catalog and dependency locking. 

## Issue Description

The identified problem occurs when a project utilizes both version catalog and dependency locking. Specifically, if dependencies are locked using dependency locking and a change is made to a dependency version in the version catalog, the dependencies are still updated according to the lock, contrary to the expected behavior.

## How to Reproduce the Issue

To reproduce the issue in your environment, follow these steps:

1. Clone the repository.
2. Build the project using ./gradlew build.
3. Check the dependencies in build scan > dependencies. Hamcrest is set to 2.2.

Note: app/gradle.lockfile has hamcrest version locked at v2.2 and in gradle/libs.toml.version, hamcrest library is manually set to v2.1. This version mismatch should have thrown an error.

## Expected Behavior

The expected behavior is that when dependencies are locked using dependency locking and a change is made to a dependency version in the version catalog, the dependencies should not be updated, and the build should fail.

## Current Behavior

Currently, despite the use of dependency locking, a change in a dependency version within the version catalog does not prevent the dependencies from being updated as per the lock. The behavior is inconsistent with expectations.
