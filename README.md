# Silk Wagmi Connector

This package contains the wagmi connector for Silk which allows users to
use regualar wagmi hooks in their app to integrate the Silk SDK.

## Documentation

- The constructor can optionally take a Silk referral code as parameter.
- Put the connector in your wagmiConfig to enable automatic re-connect on page load

```js
const wagmiConfig: Config = createConfig({
  chains: [mainnet],
  connectors: [silk({ referralCode: 'xyz', config: { appName: 'My App', appLogo: 'https://path-to-my-logo', darkMode: true } })],
```

Two options to establish a connection:

```js
const { connect, error, connectors } = useConnect()

// use the connector from wagmi config:
const silkConnector = connectors.find((connector) => connector.id === 'silk')
connect({ chainId: silkConnector.getChainId(), connector: silkConnector })
// or connect dynamically
connect({ chainId: optimism, connector: silk() })
```
