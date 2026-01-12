## Third-Party APIs & SDKs Used

### 1. Blockchain & Web3 Infrastructure

#### Ethereum Mainnet
- **Purpose:** Production blockchain network for real MNEE token transactions  
- **License:** Public blockchain (open access)  
- **Documentation:** https://ethereum.org  
- **Used for:**  
  - Smart contract execution  
  - Transaction settlement  

#### MNEE Token (ERC-20)
- **Contract Address:** `0x8ccedbAe4916b79da7F3F612EfB2EB93A2bFD6cF`  
- **Purpose:** USD-backed stablecoin for tourism payments  
- **License:** ERC-20 standard (public interface)  
- **Used for:**  
  - Payment escrow  
  - Automated revenue splits  
  - Treasury management  

#### Infura
- **Purpose:** Ethereum node infrastructure provider  
- **License:** Commercial API (API key required)  
- **Documentation:** https://infura.io  
- **Used for:**  
  - RPC endpoints for blockchain interactions  
- **Note:** API key configured for production access  

---

### 2. Wallet & Authentication

#### MetaMask
- **License:** MIT License (open source)  
- **Documentation:** https://metamask.io  
- **GitHub:** https://github.com/MetaMask  
- **Used for:**  
  - Wallet connection  
  - Transaction signing  
  - User authentication  

#### WalletConnect
- **License:** GPL-3.0 License (open source)  
- **Documentation:** https://walletconnect.com  
- **GitHub:** https://github.com/WalletConnect  
- **Used for:**  
  - Multi-wallet support  
  - Mobile wallet connections  

#### OnchainKit by Coinbase / Base *(Prepared for Future Use)*
- **Version:** 1.1.1  
- **License:** MIT License  
- **Documentation:** https://onchainkit.xyz  
- **GitHub:** https://github.com/coinbase/onchainkit  
- **Package:** `@coinbase/onchainkit@^1.1.1`  
- **Used for:**  
  - Base L2 integration (ready for deployment)  
  - Smart wallet and gasless transaction support  

---

### 3. Web3 Libraries

#### Wagmi
- **Version:** 2.18.2  
- **License:** MIT License  
- **Documentation:** https://wagmi.sh  
- **GitHub:** https://github.com/wevm/wagmi  
- **Package:** `wagmi@^2.18.2`  
- **Used for:**  
  - React hooks for Ethereum wallet management  

#### Viem
- **Version:** 2.38.4  
- **License:** MIT License  
- **Documentation:** https://viem.sh  
- **GitHub:** https://github.com/wevm/viem  
- **Package:** `viem@^2.38.4`  
- **Used for:**  
  - TypeScript Ethereum interactions  
  - ABI encoding and decoding  

#### Ethers.js
- **Version:** 6.x  
- **License:** MIT License  
- **Documentation:** https://docs.ethers.org  
- **GitHub:** https://github.com/ethers-io/ethers.js  
- **Package:** `ethers@^6`  
- **Used for:**  
  - Smart contract interactions  
  - Transaction construction  

---

### 4. Farcaster Integration

#### Farcaster MiniApp SDK
- **Version:** 0.2.1  
- **License:** MIT License (open source)  
- **Documentation:** https://docs.farcaster.xyz  
- **GitHub:** https://github.com/farcasterxyz/miniapp-sdk  
- **Package:** `@farcaster/miniapp-sdk@^0.2.1`  
- **Used for:**  
  - Farcaster Frame metadata  
  - Mini-app functionality  

---

### 5. Frontend Framework & UI

#### Next.js
- **Version:** 15.3.8+  
- **License:** MIT License  
- **Documentation:** https://nextjs.org  
- **GitHub:** https://github.com/vercel/next.js  
- **Used for:**  
  - React framework  
  - Routing and server-side rendering  

#### React
- **Version:** 19.x  
- **License:** MIT License  
- **Documentation:** https://react.dev  
- **GitHub:** https://github.com/facebook/react  
- **Used for:**  
  - UI component development  

#### Tailwind CSS
- **Version:** 4.x  
- **License:** MIT License  
- **Documentation:** https://tailwindcss.com  
- **GitHub:** https://github.com/tailwindlabs/tailwindcss  
- **Used for:**  
  - Utility-first responsive styling  

#### shadcn/ui
- **License:** MIT License (open source)  
- **Documentation:** https://ui.shadcn.com  
- **GitHub:** https://github.com/shadcn-ui/ui  
- **Used for:**  
  - Accessible and reusable React components  

#### Lucide React
- **License:** ISC License (open source)  
- **Documentation:** https://lucide.dev  
- **GitHub:** https://github.com/lucide-icons/lucide  
- **Used for:**  
  - Icon library  

---

### 6. State Management & Data Fetching

#### TanStack Query (React Query)
- **Version:** 5.66.0+  
- **License:** MIT License  
- **Documentation:** https://tanstack.com/query  
- **GitHub:** https://github.com/TanStack/query  
- **Package:** `@tanstack/react-query@^5.66.0`  
- **Used for:**  
  - Asynchronous state management  
  - Data fetching and caching  

---

### 7. TypeScript & Build Tools

#### TypeScript
- **License:** Apache License 2.0  
- **Documentation:** https://www.typescriptlang.org  
- **GitHub:** https://github.com/microsoft/TypeScript  
- **Used for:**  
  - Type-safe JavaScript development  

---

## License & Permission Summary

✅ **Open-Source Licenses Used**
- MIT License (majority of libraries)  
- Apache License 2.0 (TypeScript)  
- ISC License (Lucide)  
- GPL-3.0 License (WalletConnect)  

✅ **Commercial APIs with Proper Authentication**
- Infura (API key configured)  
- Ethereum Mainnet (public blockchain)  

✅ **Compliance & Transparency**
- All dependencies installed via npm/pnpm include license files  
- License information available in:  
  - `package.json`  
  - `node_modules/[package]/LICENSE`  
- All libraries are publicly available and well-documented  
- No proprietary or restricted APIs were used without permission  

---

**Repository Compliance Note:**  
This project fully complies with hackathon and open-source usage requirements. All third-party dependencies are properly licensed, documented, and publicly accessible.
