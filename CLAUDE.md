# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**aerie-time-utils** is a TypeScript library providing utility functions for working with dates and times in the Aerie ecosystem. It is published as `@nasa-jpl/aerie-time-utils` and is part of the NASA-AMMOS project.

The library handles various date formats including:
- ISO Ordinal time (YYYY-DDDTHH:mm:ss.SSS)
- ISO 8601 UTC time (YYYY-MM-DDTHH:mm:ssZ)
- DOY (Day of Year) duration strings
- PostgreSQL interval format
- Human-readable duration strings (e.g., "1d 2h 30m")
- Microsecond precision timestamps

## Build and Test Commands

```bash
# Install dependencies
npm install

# Build both CJS and ESM modules
npm run build

# Run tests with Vitest
npm run test

# Clean dist folder
npm run clean

# Format code with Prettier
npm run reformat
```

## Project Structure

```
src/
├── index.ts              # Main exports file
├── timeUtils.ts          # Core time utility functions
├── timeUtils.test.ts     # Test suite (Vitest)
├── constants/
│   └── time.ts           # Regex patterns for time parsing
├── enums/
│   └── time.ts           # TimeTypes enum, TIME_MS constants
└── types/
    └── time.ts           # TypeScript type definitions
```

## Key Concepts

### Time Types (TimeTypes enum)
- `ISO_ORDINAL_TIME` - Format: `YYYY-DDDTHH:mm:ss[.mmm[uuu]]`
- `ISO_8601_UTC_TIME` - Format: `YYYY-MM-DDTHH:mm:ss[.mmm[uuu]]Z`
- `DOY_TIME` - Format: `[+/-]DDD[T]HH:mm:ss[.mmm[uuu]]`
- `SECOND_TIME` - Format: `[+/-]ss[.mmm[uuu]]`

### Core Types
- `ParsedDoyString` - Parsed ISO Ordinal date components
- `ParsedYmdString` - Parsed ISO 8601 date components
- `ParsedDurationString` - Parsed duration with all time units
- `DurationTimeComponents` - String-formatted duration components

## Code Conventions

- Uses ES modules with `.js` extensions in imports (for ESM compatibility)
- Exports both CommonJS (`dist/cjs`) and ESM (`dist/esm`) builds
- All time parsing functions support microsecond precision
- Functions throw descriptive errors for invalid time formats
- Uses `lodash-es` for string utilities and `postgres-interval` for interval parsing
- All functions include JSDoc documentation with examples
