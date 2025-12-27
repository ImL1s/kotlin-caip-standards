# Kotlin CAIP Standards

Kotlin Multiplatform implementation of [Chain Agnostic Improvement Proposals (CAIP)](https://github.com/ChainAgnostic/CAIPs) standards.

## Supported Standards

- **CAIP-2**: Blockchain ID Specification (e.g., `eip155:1` for Ethereum mainnet)
- **CAIP-10**: Account ID Specification (e.g., `eip155:1:0x...`)
- **CAIP-19**: Asset Type and Asset ID Specification

## Installation

Add JitPack repository to your project:

```kotlin
// settings.gradle.kts
dependencyResolutionManagement {
    repositories {
        maven { url = uri("https://jitpack.io") }
    }
}
```

Add the dependency:

```kotlin
// build.gradle.kts
dependencies {
    implementation("com.github.iml1s:kotlin-caip-standards:1.0.0")
}
```

## Usage

```kotlin
import io.github.iml1s.caip.*

// Parse a CAIP-2 chain ID
val chainId = ChainId.parse("eip155:1")
println(chainId.namespace) // "eip155"
println(chainId.reference) // "1"

// Parse a CAIP-10 account ID
val accountId = AccountId.parse("eip155:1:0x1234...")
println(accountId.chainId) // ChainId("eip155", "1")
println(accountId.address) // "0x1234..."

// Parse a CAIP-19 asset ID
val assetId = AssetId.parse("eip155:1/erc20:0xdAC17F958D2ee523a2206206994597C13D831ec7")
println(assetId.chainId) // ChainId("eip155", "1")
println(assetId.assetType) // "erc20"
println(assetId.tokenId) // "0xdAC17F958D2ee523a2206206994597C13D831ec7"
```

## Platform Support

- Android
- iOS (arm64, x64, simulatorArm64)
- watchOS (arm32, arm64, x64, simulatorArm64)
- JVM

## License

Apache License 2.0
