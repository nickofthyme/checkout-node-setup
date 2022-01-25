# Checkout node setup

This action combines [`actions/checkout`](https://github.com/actions/checkout), [`actions/setup-node`](https://github.com/bahmutov/npm-install) and [`bahmutov/npm-install`](https://github.com/bahmutov/npm-install) into a single action.

## Inputs

### `skip-checkout`

Skips the checkout step

### `skip-setup-node`

Skips the node setup step

### `skip-npm-install`

Skips the npm install step

## Extended Inputs

All inputs from the three actions are mapped 1:1 as they would be used on their own, with the following exceptions:

### `checkout-token`

Used as the `token` input for `actions/checkout`

### `setup-node-token`

Replaces the `token` input for `actions/setup-node`

### `persist-credentials` from `actions/checkout`

Defaults to `false` instead of `true`

### `node-version` from `actions/setup-node`

Defaults to `env.NODE_VERSION` instead of `undefined`

### `useRollingCache` from `bahmutov/npm-install`

Defaults to `true` instead of `false`


## Outputs

None! :tada:

## Example usage

### Before

```yaml
- name: Checkout
  uses: actions/checkout@v2
  with:
    persist-credentials: false
- name: Setup node
  uses: actions/setup-node@v2
  with:
    node-version: ${{ env.NODE_VERSION }}
- name: Install node_modules
  uses: bahmutov/npm-install@v1
  with:
    useRollingCache: true
```

### After

```yaml
- name: Setup job
  uses: nickofthyme/checkout-node-setup@v1
  with:
    persist-credentials: false
    useRollingCache: true
```
