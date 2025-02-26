# install DuckDB

- command line on dir 'thoregon.modules/thoregon.neuland'
> npm install

# modify agent agent_0_config.mjs

import OLAPService              from "/thoregon.neuland/src/olap/olapservice.mjs";

## vendor agent config:

add service:


        olap: {
            producer: OLAPService,
            settings: {
                db       : 'upayme',
                version  : 1,
                upcmds   : [],
                downcmds : [],
                migration: {
                    1: [
                        { sql: 'CREATE SEQUENCE IF NOT EXISTS txid START 1;'},
                        {
                            table: 'transactions', columns: [
                                { name: 'txid', def: "INTEGER DEFAULT nextval('txid')" },
                                { name: 'business_index', def: 'INTEGER NOT NULL' },
                                { name: 'transaction_id', def: 'VARCHAR' },
                                { name: 'type', def: 'VARCHAR' },
                                { name: 'txdate', def: 'TIMESTAMP' },
                                { name: 'order_id', def: 'VARCHAR' },
                                { name: 'orderitem_id', def: 'VARCHAR' },
                                { name: 'order_docnum', def: 'VARCHAR' },
                                { name: 'invoice_id', def: 'VARCHAR' },
                                { name: 'invoice_docnum', def: 'VARCHAR' },
                                { name: 'product_id', def: 'VARCHAR' },
                                { name: 'paymentplan_id', def: 'VARCHAR' },
                                { name: 'product_name', def: 'VARCHAR' },
                                { name: 'customer_id', def: 'VARCHAR' },
                                { name: 'customer_name', def: 'VARCHAR' },
                                { name: 'customer_email', def: 'VARCHAR' },
                                { name: 'coupons', def: 'VARCHAR' },        // store list (array) of coupon names
                                { name: 'quantity', def: 'FLOAT' },
                                { name: 'total', def: 'FLOAT' },
                                { name: 'tax', def: 'FLOAT' },
                                { name: 'net_total', def: 'FLOAT' },
                                { name: 'coupons_amount', def: 'FLOAT' },
                                { name: 'affiliate_amount', def: 'FLOAT' },
                                { name: 'partner_amount', def: 'FLOAT' },
                                { name: 'payment_provider', def: 'VARCHAR' },
                                { name: 'provider_type', def: 'VARCHAR' },
                                { name: 'payment_type', def: 'VARCHAR' },
                                { name: 'transaction_fees', def: 'FLOAT' },
                                { name: 'upayme_fees', def: 'FLOAT' },
                                { name: 'earnings', def: 'FLOAT' },
                                { name: 'currency', def: 'VARCHAR' },
                                { name: 'refundtransaction_id', def: 'VARCHAR' },
                                { name: 'paymenttransaction_id', def: 'VARCHAR' },
                                { name: 'message', def: 'VARCHAR' },
                                { def: 'PRIMARY KEY (txid)' },

                                { cmd: 'CREATE UNIQUE INDEX IF NOT EXISTS busevtidx ON transactions (business_index)' },
                                { cmd: 'CREATE UNIQUE INDEX IF NOT EXISTS txid ON transactions (transaction_id)' },
                            ]
                        },
                        { sql: 'CREATE OR REPLACE VIEW tx_analysis AS SELECT year(txdate) as year, month(txdate) as month, week(txdate) as week, * FROM transactions' }
                    ]
                },
            }
        },

## nexus agent config:

add service:


        olap: {
            producer: OLAPService,
            settings: {
                db       : 'upayme',
                version  : 1,
                upcmds   : [],
                downcmds : [],
                migration: {
                    1: [
                        { sql: 'CREATE SEQUENCE IF NOT EXISTS acid START 1;'},
                        { table: 'activities', columns: [
                                { name: 'id', def: "INTEGER DEFAULT nextval('acid')" },
                                { name: 'action', def: 'VARCHAR' },
                                { name: 'txdate', def: 'TIMESTAMP' },
                                { name: 'vendor', def: 'VARCHAR' },
                                { name: 'product', def: 'VARCHAR' },
                                { name: 'paymentplan', def: 'VARCHAR' },
                                { name: 'affiliate', def: 'VARCHAR' },
                                { name: 'campaignkey', def: 'VARCHAR' },
                                { name: 'quantity', def: 'FLOAT' },
                                { name: 'amount', def: 'FLOAT' },
                                { name: 'currency', def: 'VARCHAR' },
                                { name: 'reengaged', def: 'BOOLEAN' },
                                { name: 'last_affiliate', def: 'VARCHAR' },
                                { name: 'last_affiliate_reengaged', def: 'VARCHAR' },
                                { def: 'PRIMARY KEY (id)' },

                                { cmd: 'CREATE INDEX idx_action ON activities (action);' },
                                { cmd: 'CREATE INDEX idx_vendor ON activities (vendor);' },
                                { cmd: 'CREATE INDEX idx_product ON activities (product);' },
                                { cmd: 'CREATE INDEX idx_paymentplan ON activities (paymentplan);' },
                                { cmd: 'CREATE INDEX idx_productplan ON activities (product, paymentplan);' },
                                { cmd: 'CREATE INDEX idx_affiliate ON activities (affiliate);' },
                                { cmd: 'CREATE INDEX idx_campaignkey ON activities (campaignkey);' },
                            ]
                        },
                    ]
                },
            }
        }, 
        
