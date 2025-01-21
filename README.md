# MEV Triangular Arbitrage Bot for Ethereum (PancakeSwap Flash Swap)

Welcome to the MEV Triangular Arbitrage Bot repository! This smart contract is designed to take advantage of **Maximum Extractable Value (MEV)** opportunities through **Triangular Arbitrage** on decentralized exchanges (DEX) like **PancakeSwap**. 

### **Key Features**:
- **Triangular Arbitrage**: The bot performs profitable triangular trades across token pairs using the PancakeSwap DEX.
- **Flash Loan Capability**: The contract can initiate **flash loans** to capitalize on arbitrage opportunities without needing upfront capital.
- **Gas Efficiency**: Optimized for gas efficiency to maximize profits during arbitrage trades.
- **Automatic Profit Check**: The bot automatically checks if the trade will be profitable before executing the arbitrage.

### **How it Works**:
1. **Flash Loans**: The contract borrows tokens using a flash loan.
2. **Triangular Trading**: It then performs a series of trades between three tokens on the PancakeSwap platform.
3. **Profit Check**: Before executing the trade, it checks if the resulting amount after all trades exceeds the borrowed amount + fee, ensuring a profitable outcome.
4. **Repayment**: The contract repays the loan after the arbitrage is successfully completed.

### **Core Functions**:

- **Funding the Contract**:
  ```solidity
  function fundFlashContract(address _owner, address _token, uint256 _amount) public
  ```
  This function allows the contract to be funded with tokens (ERC20).

- **Place Trade**:
  ```solidity
  function placeTrade(address _fromToken, address _toToken, uint256 _amountIn) private returns (uint256)
  ```
  This function executes the trade from one token to another, ensuring the best possible outcome.

- **Check Profitability**:
  ```solidity
  function checkTriangularTradeProfitabilityOnBlockCall(address _tradeToken1, address _tradeToken2, address _tradeToken3, uint256 _amount) external view returns (bool)
  ```
  It checks the profitability of a triangular arbitrage trade before executing it.

- **Start Arbitrage Trade**:
  ```solidity
  function pancakeCall(address _sender, uint256 _amount0, uint256 _amount1, bytes calldata _data) external
  ```
  Executes the arbitrage, ensuring that the final outcome is profitable and the flash loan is repaid.

### **Workflow**:
1. The bot receives **tokens** into the contract and initiates a **flash loan** for the necessary token.
2. The contract performs a **triangular arbitrage** between three tokens: **Token1 → Token2 → Token3 → Token1**.
3. Before proceeding, it checks if the resulting token after the arbitrage is worth more than the amount borrowed plus a small fee.
4. If profitable, it repays the **flash loan** and transfers the profit back to the owner's address.

## Contact
- **Email**: [sakelejames@gmail.com](mailto:sakelejames@gmail.com)
- **Telegram**: [@snipmaxi](https://t.me/snipmaxi)
