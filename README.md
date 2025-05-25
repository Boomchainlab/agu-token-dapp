The $AGU Token DApp is a next-generation, blockchain-native interface for interacting with the $AGU token on the Base network. It provides users with access to secure token interactions, real-time market insights, and gamified DeFi experiences through a scalable frontend and modular backend architecture.

This DApp also integrates Solana trading infrastructure via QuickNode to extend cross-chain data feeds, token swap quotes, and decentralized market interactions.

⸻

Base Chain Module (Primary Contract Layer)

The $AGU ERC20 contract is deployed on Base, Ethereum’s Layer 2 built on Optimism. The contract includes:
	•	Upgradeable token architecture (OpenZeppelin 5.x compatible)
	•	Flash minting, permit signatures, and vote delegation
	•	Owner-based mint access control
	•	Proxy-safe initializer pattern

Key Details
Name
Symbol
$AGU
AGU
Network
Base (Optimism L2)
Standard
ERC20Upgradeable

Example Contract Methods
function initialize(address initialOwner) public initializer;
function mint(address to, uint256 amount) public onlyOwner;

📌 Admin Contact: admin@boomchainlab.com
📣 Twitter: @Agunnaya001

⸻

Solana Integration Module (Cross-Chain Trading Layer)

This module equips the backend with high-performance Solana API endpoints via QuickNode, enabling powerful DEX interactions and market visualization.

Available REST Endpoints

Endpoint
Method
Description
/solana/price
GET
Retrieve current Solana price data
/solana/markets
GET
Fetch Solana market listings
/solana/new-pools
GET
List new liquidity pools on Solana
/solana/pump/quote
POST
Get pump quote for token swaps
/solana/pump/swap
POST
Generate swap instructions
/solana/limit-orders/create
POST
Create a limit order
/solana/limit-orders/open
POST
Retrieve open limit orders
/solana/limit-orders/cancel
POST
Cancel an existing limit order

Setup Instructions
	1.	Blueprint Registration

In your app.py or equivalent:
from app.solana.routes import solana_bp
app.register_blueprint(solana_bp)

2.	Environment Config
In your .env file:
QUICKNODE_API_KEY=your_quicknode_api_key_here

	3.	Run Your Flask Server

Ensure the backend loads with the correct API keys and route mappings.

⸻

Flask Blueprint: Solana Route Handler
from flask import Blueprint
from app.solana.quicknode import get_price, get_markets, get_new_pools
from app.solana.pump import get_pump_quote, get_pump_swap
from app.solana.jupiter import create_limit_order, open_orders, cancel_order

solana_bp = Blueprint('solana', __name__, url_prefix='/solana')

solana_bp.add_url_rule('/price', 'get_price', get_price, methods=['GET'])
solana_bp.add_url_rule('/markets', 'get_markets', get_markets, methods=['GET'])
solana_bp.add_url_rule('/new-pools', 'get_new_pools', get_new_pools, methods=['GET'])
solana_bp.add_url_rule('/pump/quote', 'get_pump_quote', get_pump_quote, methods=['POST'])
solana_bp.add_url_rule('/pump/swap', 'get_pump_swap', get_pump_swap, methods=['POST'])
solana_bp.add_url_rule('/limit-orders/create', 'create_limit_order', create_limit_order, methods=['POST'])
solana_bp.add_url_rule('/limit-orders/open', 'open_orders', open_orders, methods=['POST'])
solana_bp.add_url_rule('/limit-orders/cancel', 'cancel_order', cancel_order, methods=['POST'])


This README empowers developers to rapidly onboard into the $AGU ecosystem, leveraging Base for core token mechanics and Solana for liquidity analytics and real-time trading operations.
