# GOUT DEX - 去中心化交易所

GOUT是一个类似PancakeSwap的去中心化交易所(DEX)，提供代币交换、流动性提供等功能，界面采用科技感十足的深色主题设计。

![GOUT DEX界面预览](https://p3-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/super_tool/ef089e2dc93b43289a7e02dbe50619cb~tplv-a9rns2rl98-image.image?lk3s=8e244e95&rcl=20260128205153B16DA04800629D223BB7&rrcfp=f06b921b&x-expires=1772196754&x-signature=0DPVEi%2BEMjTxyDO%2BM%2BbcKHhQYpQ%3D)

## 功能特点

- **代币交换**：支持不同代币间的兑换，显示实时价格、滑点、手续费等信息
- **流动性池**：用户可添加/移除流动性，获得LP代币
- **交易历史**：记录用户的交换和流动性操作
- **价格图表**：实时展示代币价格走势
- **多链支持**：支持BNB Chain、Ethereum、Polygon、Avalanche等多个区块链网络
- **钱包集成**：支持MetaMask、Trust Wallet、Coinbase Wallet等主流钱包

## 技术栈

- **前端框架**：纯HTML5 + CSS3 + JavaScript
- **CSS框架**：Tailwind CSS v3
- **图标库**：Font Awesome 4.7.0
- **图表库**：Chart.js (用于价格图表展示)

## 安装与部署

### 本地开发

1. 克隆项目到本地

```bash
git clone https://github.com/yourusername/gout-dex.git
cd gout-dex
```

2. 启动本地服务器

```bash
# 使用Python内置服务器
python -m http.server 8000

# 或使用Node.js的http-server
npx http-server -p 8000
```

3. 在浏览器中访问 `http://localhost:8000`

### 生产环境部署

由于这是一个纯前端项目，您可以将其部署到任何静态网站托管服务上。

#### 选项1：GitHub Pages

1. 将项目推送到GitHub仓库
2. 在仓库设置中启用GitHub Pages
3. 选择分支和目录（通常是main分支和根目录）
4. 保存设置，GitHub会自动部署您的网站

#### 选项2：Vercel

1. 注册Vercel账号
2. 连接您的GitHub仓库
3. 选择要部署的仓库
4. 点击"Deploy"按钮
5. 部署完成后，您将获得一个Vercel提供的域名

#### 选项3：Netlify

1. 注册Netlify账号
2. 拖拽项目文件夹到Netlify界面，或连接GitHub仓库
3. 配置构建设置（对于纯前端项目，通常不需要特殊配置）
4. 点击"Deploy site"按钮
5. 部署完成后，您将获得一个Netlify提供的域名

#### 选项4：IPFS/去中心化存储

1. 安装IPFS CLI或使用Pinata等服务
2. 上传项目文件夹到IPFS
3. 获取IPFS哈希值
4. 使用IPFS网关或ENS域名访问您的网站

## 自定义配置

### 修改代币列表

在`index.html`文件中，找到`tokens`数组，您可以添加或修改代币信息：

```javascript
const tokens = [
    { symbol: 'BNB', name: 'BNB', balance: 100.00, price: 312.45, color: 'bg-blue-500' },
    { symbol: 'CAKE', name: 'CAKE', balance: 500.00, price: 1.24, color: 'bg-purple-500' },
    // 添加更多代币...
];
```

### 修改颜色主题

在`index.html`文件中，找到Tailwind配置部分，您可以修改颜色变量：

```javascript
tailwind.config = {
    theme: {
        extend: {
            colors: {
                primary: '#00F0FF',  // 主要颜色
                secondary: '#9D4EDD', // 次要颜色
                dark: '#0A0E29',      // 深色背景
                // 修改其他颜色...
            },
            // ...
        }
    }
}
```

## 与Web3集成

当前版本是一个前端演示，要与真实区块链集成，您需要：

1. 添加Web3库（如Web3.js或ethers.js）

```html
<script src="https://cdn.jsdelivr.net/npm/web3@1.7.0/dist/web3.min.js"></script>
<!-- 或 -->
<script src="https://cdn.jsdelivr.net/npm/ethers@5.5.1/dist/ethers.umd.min.js"></script>
```

2. 替换模拟数据和功能为真实区块链交互

```javascript
// 连接到区块链
const web3 = new Web3(window.ethereum);

// 加载合约ABI和地址
const routerABI = [...]; // 从文件或API加载
const routerAddress = '0x...';
const routerContract = new web3.eth.Contract(routerABI, routerAddress);

// 获取代币余额
async function getTokenBalance(tokenAddress, userAddress) {
    const tokenContract = new web3.eth.Contract(erc20ABI, tokenAddress);
    const balance = await tokenContract.methods.balanceOf(userAddress).call();
    return web3.utils.fromWei(balance, 'ether');
}

// 执行代币交换
async function swapTokens(fromToken, toToken, amount, userAddress) {
    // 检查授权
    // 执行交换
    // 处理交易确认
}
```

## 安全考虑

在生产环境中部署前，请考虑以下安全措施：

1. 实施内容安全策略(CSP)
2. 启用HTTPS
3. 验证所有用户输入
4. 实施速率限制
5. 定期更新依赖库
6. 进行安全审计

## 贡献指南

欢迎贡献代码！请遵循以下步骤：

1. Fork项目
2. 创建您的特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交您的更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 打开一个Pull Request

## 许可证

本项目采用MIT许可证 - 查看[LICENSE](LICENSE)文件了解详情。

## 联系方式

如有问题或建议，请通过以下方式联系我们：

- 项目链接：[https://github.com/yourusername/gout-dex](https://github.com/yourusername/gout-dex)
- 电子邮件：contact@goutdex.io

## 免责声明

本项目仅供学习和演示目的。在实际使用中，请确保遵守相关法律法规，并自行承担所有风险。