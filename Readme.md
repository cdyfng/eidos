#Eidos contract

git clone https://github.com/enumivo/eidos.git
cd eidos/
mkdir token 
eosio-cpp token.cpp -o token/token.wasm

cleos wallet unlock -n main_wallet --password $(cat ~/main_wallet_password.txt)


cleos -u 'https://api.eosnewyork.io' set contract yourtwlvname ./token/ -p yourtwlvname@active
cleos  -u 'https://api.eosnewyork.io'  push action eosio.token create '["yourtwlvname","100000000.0000 TEST"]' -p eosio.token 
cleos push action eosio.token issue '["yourtwlvname","100.0000 TEST","test"]' -p yourtwlvname

cleos -u 'https://api.eosnewyork.io'  push action yourtwlvname create '["yourtwlvname","10000000000.0000 EIDOS"]' -p yourtwlvname 
cleos -u 'https://api.eosnewyork.io'  push action yourtwlvname issue '["yourtwlvname","1.0000 EIDOS","test"]' -p yourtwlvname 
cleos -u 'https://api.eosnewyork.io'  get table eosio.token  yourtwlvname  accounts
cleos -u 'https://api.eosnewyork.io'  get table yourtwlvname xxxxxx accounts
