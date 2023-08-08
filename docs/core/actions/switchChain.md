<script setup>
const packageName = '@wagmi/core'
const actionName = 'switchChain'
const typeName = 'SwitchChain'
</script>

# switchChain

Action for switching the target chain for a connector or the Wagmi [`Config`](/core/createConfig#config).

## Import

```ts
import { switchChain } from '@wagmi/core'
```

## Usage

::: code-group
```ts [index.ts]
import { switchChain } from '@wagmi/core'
import { mainnet } from '@wagmi/core/chains'
import { config } from './config'

await switchChain(config, { chainId: mainnet.id })
```
<<< @/snippets/core/config.ts[config.ts]
:::

::: tip
When connected, `switchChain` will switch the target chain for the connector. When not connected, `switchChain` will switch the target chain for the Wagmi [`Config`](/core/createConfig#config).
:::

## Parameters

```ts
import { type SwitchChainParameters } from '@wagmi/core'
```

### chainId

`config['chains'][number]['id'] | undefined`

ID of chain to switch to.

::: code-group
```ts [index.ts]
import { switchChain } from '@wagmi/core'
import { mainnet } from '@wagmi/core/chains'
import { config } from './config'

const result = await switchChain(config, {
  chainId: mainnet.id, // [!code focus]
})
```
<<< @/snippets/core/config.ts[config.ts]
:::

### connector

`Connector`

[Connector](/core/connectors) to switch chain with.

::: code-group
```ts [index.ts]
import { getConnections, switchAccount } from '@wagmi/core'
import { mainnet } from '@wagmi/core/chains'
import { config } from './config'

const connections = getConnections(config)
const result = await switchChain(config, {
  chainId: mainnet.id,
  connector: connections[0]?.connector, // [!code focus]
})
```
<<< @/snippets/core/config.ts[config.ts]
:::

## Return Type

```ts
import { type SwitchChainReturnType } from '@wagmi/core'
```

`Chain`

Chain that was switched to.

## Error

```ts
import { type SwitchChainError } from '@wagmi/core'
```

<!--@include: @shared/mutation-imports.md-->

## Viem

[`switchChain`](https://viem.sh/docs/actions/wallet/switchChain.html) when connected.