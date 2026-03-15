# soroban-react

> React hooks for Soroban smart contracts on Stellar. Build dApps without the boilerplate.

`soroban-react` is an open-source library that gives React developers a composable, type-safe interface for interacting with Soroban contracts on Stellar — wallet connection, contract reads/writes, and transaction lifecycle, all in simple hooks.

```tsx
const { invoke, isPending } = useContractWrite({
  contractId: "CABC...",
  method: "transfer",
});

await invoke({ to: recipient, amount: 100n });
```

---

## Packages

| Package | Description |
|---|---|
| `@soroban-react/core` | Core hooks: `useWallet`, `useContractRead`, `useContractWrite`, `useTransaction`, `useNetwork` |
| `@soroban-react/freighter` | Freighter wallet adapter |

---

## Features

- 🔌 **Wallet-agnostic** — plug in Freighter or any SEP-0007 compatible wallet
- 📖 **Contract reads** — query Soroban contract state reactively
- ✍️ **Contract writes** — invoke contracts with full transaction lifecycle (idle → pending → success/error)
- 🔒 **Type-safe** — TypeScript generics map your contract's ABI to hook inputs/outputs
- ⚡ **Lightweight** — zero heavy dependencies; built on `@stellar/stellar-sdk`

---

## Quick Start

```bash
npm install @soroban-react/core @soroban-react/freighter
```

```tsx
import { SorobanProvider } from "@soroban-react/core";
import { freighter } from "@soroban-react/freighter";

function App() {
  return (
    <SorobanProvider
      network="testnet"
      rpcUrl="https://soroban-testnet.stellar.org"
      wallets={[freighter()]}
    >
      <YourApp />
    </SorobanProvider>
  );
}
```

---

## Hooks

### `useWallet()`
Connect and manage wallet state.

```tsx
const { address, connect, disconnect, isConnected } = useWallet();
```

### `useContractRead({ contractId, method, args })`
Read contract state. Re-fetches on network/account changes.

```tsx
const { data, isLoading } = useContractRead({
  contractId: "CABC...",
  method: "balance",
  args: [address],
});
```

### `useContractWrite({ contractId, method })`
Invoke a contract method and track the transaction.

```tsx
const { invoke, isPending, isSuccess, error } = useContractWrite({
  contractId: "CABC...",
  method: "transfer",
});
```

### `useNetwork()`
Get active network config and switch networks.

```tsx
const { network, rpcUrl } = useNetwork();
```

### `useTransaction(hash)`
Poll and track any transaction by hash.

```tsx
const { status, result } = useTransaction(txHash);
```

---

## Contributing

This project is actively developed as part of the **Stellar Wave on drips.network**.  
Browse [open issues](../../issues) to find Wave bounties — good first issues are labelled `wave:easy`.

See [CONTRIBUTING.md](./CONTRIBUTING.md) to get set up locally.

---

## License

MIT
