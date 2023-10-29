# Candy Machine Windows Edition! Launch Solana NFT Collection with Metaplex Candy Machine V3 and Sugar

# Install Git
# https://git-scm.com/download/win
git --version

# Install Node
# https://nodejs.org/en/download
npm --version

# Install Solana Tool Suite
# https://docs.solana.com/cli/install-solana-cli-tools#windows
cmd /c "curl https://release.solana.com/v1.15.2/solana-install-init-x86_64-pc-windows-msvc.exe --output C:\solana-install-tmp\solana-install-init.exe --create-dirs"
solana --version
solana-keygen --version

# Download Sugar
# https://github.com/metaplex-foundation/sugar/releases/tag/sugar-cmv3-alpha.3
./sugar --version

# Get current directory
# C:\Users\samue\Desktop\solana-module
pwd

## pubkey: EAdG42wyV8vq2N7dNVrvVQtQToyFWrBjyySz7p9i6SNw
## Keyphrase: broccoli retire advice piece wait inquiry hollow exist scan mother gym museum
solana-keygen new --outfile C:\Users\samue\Desktop\solana-module\Owner.json

## pubkey: VuRGVytox5Hq7tR26S2k3Hk4MJFpbVWRbX9QYpteBGL
## keyphrase: obey humor impulse body foam holiday leave legend ripple middle choice mother>
solana-keygen new --outfile C:\Users\samue\Desktop\solana-module\Secret.json

solana config set --keypair C:\Users\samue\Desktop\solana-module\Owner.json
solana config set --url https://frequent-hidden-pool.solana-devnet.quiknode.pro/0714255c135b4eb0e920fc69ce471342d93040db/
solana config get

solana airdrop 2 EAdG42wyV8vq2N7dNVrvVQtQToyFWrBjyySz7p9i6SNw --url https://api.devnet.solana.com
solana airdrop 2 VuRGVytox5Hq7tR26S2k3Hk4MJFpbVWRbX9QYpteBGL --url https://api.devnet.solana.com
solana airdrop 1 EAdG42wyV8vq2N7dNVrvVQtQToyFWrBjyySz7p9i6SNw --url https://api.devnet.solana.com

solana balance EAdG42wyV8vq2N7dNVrvVQtQToyFWrBjyySz7p9i6SNw
solana balance VuRGVytox5Hq7tR26S2k3Hk4MJFpbVWRbX9QYpteBGL

# Download Metaplex Sample NFT Collection
# https://docs.metaplex.com/programs/candy-machine/how-to-guides/my-first-candy-machine-part1#set-up-your-project
# https://docs.metaplex.com/assets/files/assets-ff6bd873ecd07b49c86faf3c7aab82d2.zip
Invoke-WebRequest -Uri https://docs.metaplex.com/assets/files/assets-ff6bd873ecd07b49c86faf3c7aab82d2.zip -OutFile ./assets.zip
Expand-Archive ./assets.zip 

# Create Candy Machine Config File
./sugar create-config

# Upload assets
-> pubkey: EAdG42wyV8vq2N7dNVrvVQtQToyFWrBjyySz7p9i6SNw
  -> lamports: 123760 (◎ 0.00012376)
Signature: 2bSxfE6hxBBetju8ZBRMXN7ocNLj2c5mkZCbFvx72g1bNKn163jqEp5anwnySectTHwv4kzGZXiQWUky2r7cCPC4
./sugar upload

# Deploy Candy Machine
## Collection mint ID: HkyXu4nRXX6nczMW19VUv94kprxxcujnQGN8zzBTZ58h
## Candy machine ID: 7EcLinFvpkraDKTNKvJXnvZZBJEcWSF9LWkFjCvwpXv2
./sugar deploy

# Verify Candy Machine Deployment and Setup
./sugar verify

# Add Candy Guards
./sugar guard add
./sugar guard show

# Setup KeyStrokes Candy Machine UI
Expand-Archive "./Candy Machine UI - V1.zip" -DestinationPath ./
cd '.\Candy Machine UI - V1\'
cp .\.env.example .env
# Update .env file with Candy Machine
npm install
npm run dev