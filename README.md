# 实用 Solidity 模式
---

这个仓库会持续收录一些在现实生产开发过程中有用或者比较巧妙的 Solidity/EVM 模式。相关的内容会使用尽可能地用通俗易懂的方式来编写，以便降低阅读者的技术门槛。同时每个模式的文档都会附带简单, 可运行的代码示例和测试来更好地说明。

*仓库下所有的代码示例都只是教育用途，某些地方为了更清晰地展示概念甚至放弃了最佳实践，所以它们不应该在没有经过严格检查的情况下就直接应用到生产环境中。*


## [Solidity 模式](./patterns)
- [带选择器的 ABI-encoding 数据的解码](./patterns/abi-decode-with-selector/)
    - 用来解码函数调用以及错误信息的技术。
- [错误处理进阶](./patterns/error-handling)
    - 对其他合约抛出的错误进行适当的处理以提升代码的健壮性。
- [汇编技巧-1](./patterns/assembly-tricks-1)
    - 一些精简、有效的汇编技巧, 有助于节省 gas 的同时绕开一些 Solidity 语言本身的限制。
- [代理模式基础](./patterns/basic-proxies)
    - 可升级合约相关的逻辑。
- [较大数据的存储 (SSTORE2)](./patterns/big-data-storage)
    - 一种更加节省 gas 的利用链上合约代码存储空间来储存任意数据（并可被合约读取）的方法，对较大的多词数据尤为有效。
- [先提交 + 再揭晓](./patterns/commit-reveal)
    - 用一种“分两步走”的交易处理模式来产生“半模糊”的链上行为，用来防止抢跑交易和跟随交易。
- [EIP712 链下消息签名](./patterns/eip712-signed-messages)
    - 可供人理解的 JSON 格式的信息在链下被签名，随后可在链上执行。
- [ERC20 的（不）兼容性](./patterns/erc20-compatibility)
    - 正确地兼容符合标准规范和不符合标准规范（比你想象中更加常见的）的 ERC20 代币实现。
- [ERC20 代币的 EIP2612 授权许可](./patterns/erc20-permit)
    - 先授权再转移 ERC20 代币仅需要*一笔*链上交易。
- [`eth_call` 技巧](./patterns/eth_call-tricks)
    - 使用 `eth_call` 执行快速且复杂的链上数据查询以及零成本的调用模拟。
- [显式存储桶](./patterns/explicit-storage-buckets)
    - 为可升级合约提供更安全、有保证的非重叠存储。
- [个人钱包地址（非合约地址）类型检查](./patterns/eoa-checks)
    - 介绍与个人地址和合约地址交互会产生的不同后果以及如何甄别这两种地址。
- [工厂证明](./patterns/factory-proofs)
    - 在链上证明合约是由可信任的部署人部署的。
- [初始化可升级合约](./patterns/initializing-upgradeable-contracts)
    - 安全且高效地为代理合约初始化变量的方法。
- [默克尔证明](./patterns/merkle-proofs)
    - 证明潜在大型固定集合成员资格的高效存储方法。
- [Multicall](./patterns/multicall)
    - 允许用户在单次交易中任意组合和执行多个操作。
- [NFT 接收钩子](./patterns/nft-receive-hooks)
    - 使用 ERC721/ERC1155 转移回调以避免用户提前设置限额。
- [链下存储](./patterns/off-chain-storage)
    - 通过将合约状态移出链下，极大地降低 gas 成本。
- [仅允许委托调用 / 不允许委托调用](./patterns/only-delegatecall-no-delegatecall/)
    - 限制函数是否只能在委托调用上下文中调用。
- [打包存储](./patterns/packing-storage)
    - 编排存储变量，以减少昂贵的存储访问。
- [Permit2](./patterns/permit2)
    - 适用于所有（传统和现代）ERC20 的方式安全地转移代币，无需直接授权额度。
- [只读委托调用](./patterns/readonly-delegatecall)
    - 以只读方式执行合约中的任意委托调用，并不会产生副作用。
- [将授权转账权限的合约单独抽象出来](./patterns/separate-allowance-targets/)
    - 避免在某个被授权了转账权限的合约升级时不得不迁移过去进行的授权。
- [堆栈过深的解决方案](./patterns/stack-too-deep/)
    - 避免堆栈过深错误的简洁解决方案。简洁到你无论如何都应该这么做！
- 持续关注，会有更多模式更新进来 😉

## 安装、构建、测试

在开始之前确保你已经安装了最新版本的 [foundry](https://book.getfoundry.sh/getting-started/installation)。

```bash
# Clone the repo
$> git clone git@github.com:dragonfly-xyz/useful-solidity-patterns.git
# Install foundry dependencies
$> forge install
# Run tests
$> forge test -vvv
# Run forked tests
$> forge test -vvv --fork-url $YOUR_NODE_RPC_URL -m testFork
```

## 感谢
本仓库是 [useful-solidity-patterns](https://github.com/dragonfly-xyz/useful-solidity-patterns/tree/main) 的中文译本，非常感谢 [dragonfly_xyz](https://twitter.com/dragonfly_xyz) 为社区贡献了这么优质的内容。
