<script setup>
const packageName = 'wagmi'
const mutate = 'connect'
const TData = '{ accounts: readonly Address[]; chainId: number; }'
const TError = 'ConnectError'
const TVariables = '{ chainId?: number | undefined; connector?: CreateConnectorFn | Connector | undefined; }'
</script>

# useConnect

Hook for connecting accounts with [connectors](/react/connectors). Uses the [`connect`](/core/actions/connect) action.

## Import

```ts
import { useConnect } from 'wagmi'
```

## Usage

::: code-group
```tsx [index.tsx]
import { useConnect } from 'wagmi'
import { injected } from 'wagmi/connectors'

function App() {
  const { connect } = useConnect()

  return (
    <button onClick={() => connect({ connector: injected() })}>
      Connect
    </button>
  )
}
```
<<< @/snippets/react/config.ts[config.ts]
:::

## Parameters

```ts
import { type UseConnectParameters } from 'wagmi'
```

<!--@include: @shared/mutation-options.md-->

## Return Type

```ts
import { type UseConnectReturnType } from 'wagmi'
```

### connectors

`readonly Connector[]`

Globally configured connectors via [`createConfig`](/react/createConfig#connectors). Useful for rendering a list of available connectors.

```tsx
import { useConnect } from 'wagmi'
import { mainnet } from 'wagmi/chains'
import { injected } from 'wagmi/connectors'

function App() {
  const { connect, connectors } = useConnect()

  return (
    <div>
      {connectors.map((connector) => (
        <button key={connector.id} onClick={() => connect({ connector })}>
          {connector.name}
        </button>
      ))}
    </div>
  )
}
```

<!--@include: @shared/mutation-result.md-->

::: tip
Not all connectors support connecting directly to a `chainId` (e.g. they don't support programmatic chain switching). In those cases, the connector will connect to whatever chain the connector's provider (e.g. wallet) is connected to.
:::

<!--@include: @shared/query/connect.md-->