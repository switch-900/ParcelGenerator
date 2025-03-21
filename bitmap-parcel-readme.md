# Bitmap Parcel Command Generator @switch_900 4.bitmap

A simple application for generating commands for use in ordinals to create bitmap parcels for Bitcoin Ordinals inscriptions. Use however you want and modify for your own use. 


## 📋 Overview

The Bitmap Parcel Command Generator simplifies the process of creating bitmap parcels for ordinals inscriptions by automatically generating the necessary YAML configuration and shell commands based on transaction data from a specified Bitcoin block.

This tool is designed for ordinals enthusiasts who want to efficiently create bitmap parcels without manual configuration.

## ✨ Features

- **Block Data Fetching**: Automatically retrieves and processes Bitcoin block data
- **Pattern Visualization**: Visual representation of the transaction pattern with size distribution
- **Selective Parcel Creation**: Filter out specific parcel sizes you don't want to create
- **Command Generation**: Creates all necessary commands for file creation, configuration, and execution
- **YAML Configuration**: Generates proper YAML for the `ord wallet batch` command
- **Statistics**: View distribution of parcel sizes and estimated fees
- **Light/Dark Mode**: Adjustable theme for comfortable viewing
- **Responsive Design**: Works on desktop and mobile devices
- **Data Persistence**: Saves your configuration between sessions
- **Easy Copy Functions**: One-click copy for all generated commands

## 🔧 Installation

This is a standalone HTML application that can be run directly in your browser. To install:

1. **Download the HTML file**
   - Save the `index.html` file to your local machine

2. **Open in a browser**
   - Double-click the file to open it in your default browser
   - Or right-click and select "Open with" to choose a specific browser

No server or additional installation is required.

## 🚀 Usage Guide

### Basic Operation

1. **Enter Configuration Details**:
   - **Parent Inscription ID**: The ordinals inscription ID that will be the parent for your parcels
   - **Bitmap Number**: The Bitcoin block number to use for the pattern
   - **Fee Rate**: Transaction fee rate in sats/vB

2. **Filter Parcel Sizes** (Optional):
   - Check the numbers you want to exclude from the generated parcels

3. **Generate Pattern**:
   - Click the "Generate" button to fetch and process the block data
   - Review the pattern visualization and statistics

4. **Review Parcels**:
   - The "Parcel Table" tab shows all parcels that will be created
   - You can specify destination addresses for individual parcels if needed

5. **Generate Commands**:
   - Click "Generate YAML & Commands" to create the configuration and shell commands
   - Review the YAML configuration in the "YAML Config" tab
   - Copy the necessary commands from the "Commands" tab

### Using Generated Commands

1. **Create Files**:
   - Copy and paste the commands from the "Create Commands" section into your terminal
   - This will create all necessary text files and the YAML configuration

2. **Execute Batch Command**:
   - Copy and execute the final command to process the parcels with ord
   - `ord wallet batch --fee-rate <rate> --batch <number>.yaml`

3. **Cleanup** (Optional):
   - Use commands from the "Delete Commands" section to remove temporary files

## 💡 How It Works

The tool follows these steps to generate bitmap parcels:

1. **Fetch Block Data**: Retrieves transaction data from the Bitcoin blockchain for the specified block
2. **Calculate Pattern**: Determines parcel sizes based on transaction output values
3. **Filter Pattern**: Removes any parcel sizes that have been deselected
4. **Generate Files**: Creates configuration for text files needed for each parcel
5. **Build YAML**: Constructs proper YAML configuration for the ord batch command
6. **Create Commands**: Generates shell commands for file creation, execution, and cleanup

## ⚙️ Technical Details

### Parcel Size Determination

Parcel sizes (1-9) are determined by the total BTC value of transactions:

- Size 1: 0 to 0.01 BTC
- Size 2: 0.01 to 0.1 BTC
- Size 3: 0.1 to 1 BTC
- Size 4: 1 to 10 BTC
- Size 5: 10 to 100 BTC
- Size 6: 100 to 1,000 BTC
- Size 7: 1,000 to 10,000 BTC
- Size 8: 10,000 to 100,000 BTC
- Size 9: More than 100,000 BTC

### File Format

Generated bitmap files follow this naming convention:
`<transaction_index><block_number>bitmap.txt`

Each file contains a single line with this format:
`<transaction_index>.<block_number>.bitmap`

### YAML Configuration

The YAML configuration follows the ord batch format:
```yaml
mode: separate-outputs
parent: <parent_inscription_id>
postage: 546
inscriptions:
  - file: <filename>
    destination: <optional_address>
  # Additional files...
```

## 🔍 Advanced Configuration

### Custom Destination Addresses

You can specify custom destination addresses for individual parcels:
1. After generating the pattern, locate the parcel in the table
2. Enter the destination address in the corresponding field
3. Generate the YAML and commands again to include these addresses

### Block Selection

The block number you choose significantly impacts the pattern:
- Recent blocks typically have more transactions
- Historical blocks may have more interesting patterns
- You can experiment with different blocks to find aesthetically pleasing patterns

## 🛠️ Troubleshooting

### Block Data Not Loading

If block data fails to load:
- Verify you entered a valid block number
- Check your internet connection
- The block may be too recent and not available through the API
- Try a different block number

### Commands Not Working

If the generated commands don't work:
- Ensure you have the ord tool installed and properly configured
- Check that you've copied the commands exactly as generated
- Verify you have sufficient funds in your ord wallet

## 📦 Dependencies

This application uses:
- Axios (v0.21.1 or higher): For blockchain API requests
- Font Awesome (v6.4.0 or higher): For icons and UI elements

These dependencies are loaded via CDN and don't require separate installation.

## 🔗 Related Resources

- [Ordinals Documentation](https://docs.ordinals.com/)
- [Ord GitHub Repository](https://github.com/casey/ord)
- [Bitcoin Block Explorer](https://blockchain.info/)

## 📄 License

This project is released under the MIT License. See the LICENSE file for details.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

---

## 📬 Contact

For questions, issues, or feature requests, please open an issue on the GitHub repository.

---

*Note: This tool interfaces with the Bitcoin blockchain and the Ordinals protocol. Always verify commands before execution and ensure you understand the implications of creating ordinals inscriptions.*
