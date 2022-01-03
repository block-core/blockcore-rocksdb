
<p align="center">
  <p align="center">
    <img src="https://user-images.githubusercontent.com/5221349/72841405-93c2ce80-3c96-11ea-844b-3e1ff782b1ae.png" height="100" alt="Blockcore" />
  </p>
  <h3 align="center">
    About Blockcore RocksDB
  </h3>
  <p align="center">
    .NET API for RocksDB
  </p>
  <p align="center">
      <a href="https://github.com/block-core/blockcore-rocksdb/actions/workflows/build.yaml"><img src="https://github.com/block-core/blockcore-rocksdb/actions/workflows/build.yaml/badge.svg" /></a>
      <a href="https://github.com/block-core/blockcore-rocksdb/actions/workflows/release.yaml"><img src="https://github.com/block-core/blockcore-rocksdb/actions/workflows/release.yaml/badge.svg" /></a>
    <a href="https://www.nuget.org/packages/Blockcore.RocksDB/"><img src="https://img.shields.io/nuget/v/Blockcore.RocksDB.svg?maxAge=0&colorB=brightgreen" /></a>
  </p>
</p>

RocksDB for .NET
----------------------------

RocksDB is a key-value database with a log-structured-merge design, optimized for flash and RAM storage,
which can be tuned to balance write-, read-, and space-amplification factors.

RocksDB is developed by Facebook and is based on LevelDB.
For more information about RocksDB, visit [RocksDB](http://rocksdb.org/) and on [GitHub](https://github.com/facebook/rocksdb).

This library provides C# bindings for RocksDB, implemented as a wrapper for the [native RocksDB libraries](https://github.com/block-core/blockcore-rocksdb-native) (unmanaged C++) via the rocksdb C API.

This is a multi-level binding, 
providing direct access to the C API functions (low level) 
plus some helper wrappers on those to aid in marshaling and exception handling (mid level) 
plus an idiomatic C# class hierarchy for ease of use (high level).

### Example (High Level)

```csharp
var options = new DbOptions()
    .SetCreateIfMissing(true);
using (var db = RocksDb.Open(options, path))
{
    // Using strings below, but can also use byte arrays for both keys and values
    db.Put("key", "value");
    string value = db.Get("key");
    db.Remove("key");
}
```
### Usage

#### Using NuGet:

[![Nuget](https://img.shields.io/nuget/v/Blockcore.RocksDB.svg?maxAge=0&colorB=brightgreen)](https://www.nuget.org/packages/Blockcore.RocksDB/) 

```
install-package Blockcore.RocksDB
```

The version of the NuGet package is set to follow the official RocksDB version, with the last number representing a revision of the .NET API itself. representing the build number on Azure - i.e. [NuGet version 6.27.3.12](https://www.nuget.org/packages/Blockcore.RocksDB/6.27.3.12) corresponds to release [v6.27.3](https://github.com/facebook/rocksdb/releases/tag/v6.27.3)

This will install the managed library and the correct version of the unmanaged library depending on your operating system. The native 64-bit library is automatically built for each official RocksDB release, for Windows, Linux and MacOS, and is included in the package by default.

## Releases

To make a new release, edit the "revision" file and commit to trigger a build that will produce a new release. Download the release artefact, verify locally, then publish the release, which will automatically publish to NuGet.org.

## Background

This library is based upon a fork of the original work by [warrenfalk](https://github.com/warrenfalk) and [theolivenbaum](https://github.com/theolivenbaum)

Due to the major modifications to the setup, including adding support for GitHub Workflows and Releases, this repository is based upon a source-copy and not a linked git-fork.

https://github.com/warrenfalk/rocksdb-sharp

https://github.com/curiosity-ai/rocksdb-sharp

## License

[BSD 2-Clause License](LICENSE)