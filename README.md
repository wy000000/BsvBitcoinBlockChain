# BsvBitcoinBlockChain
A BSV bitcoin blockchain parser (also works for BTC and BCH).

Ver 1.3.0 adds blockLength and blockchainFilename.
Ver 1.2.9 renames the block class name avoid name collision.
Ver 1.2.8 adds support for segwit blocks.
Ver 1.2.7.1 adds a nextNblockDataFiles parameter for BlockchainParser class.
	The next N blockdata files would be processed if N is assign a value. The default value is int.MaxValue.
Ver 1.2.6. This is a fork of BitcoinBlockChain (Author: Ladislau Molnar).
Version check is disabled.
Stylecop requirement is removed.

BitcoinSV. 
BSV.

            string BlockPath = System.Environment.CurrentDirectory;
            IBlockchainParser blockchainParser = new BlockchainParser(BlockPath, "blk00000.dat", 1);
            IEnumerable<ParserBlock> blocks = blockchainParser.ParseBlockchain();
            int TxCount = 0;
            int txInputCount = 0;
            int txOutputCount = 0;
            long movedAmount = 0;
            foreach (ParserBlock block in blocks)
            {
                int blocklength = block.blockLength;
                TxCount += block.Transactions.Count;
                foreach (Transaction tx in block.Transactions)
                {
                    txInputCount += tx.Inputs.Count;
                    txOutputCount += tx.Outputs.Count;
                    foreach (TxOut txout in tx.Outputs)
                    {
                        movedAmount += txout.Value.Satoshi;
                    }
                }
            }
            Console.WriteLine("block count: " + blocks.Count());
            Console.WriteLine("tx count: " + TxCount);
            Console.WriteLine("tx input count: " + txInputCount);
            Console.WriteLine("tx output count: " + txOutputCount);
            Console.WriteLine("moved amount: " + movedAmount);

Documents, please refer to https://github.com/ladimolnar/BitcoinBlockchain  .

https://www.nuget.org/packages/BsvBitcoinBlockChain/

12Nu5u5pgP7XvFGj31t71cdsmmWR7W2f83