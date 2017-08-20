#!/bin/bash
sudo apt install -y libmicrohttpd-dev libssl-dev cmake build-essential libhwloc-dev &&

git clone https://github.com/fireice-uk/xmr-stak-cpu && 

cp /dev/null donate-level.h && 

echo "#pragma once
constexpr double fDevDonationLevel = 0.0 / 100.0;" > $home/xmr-stak-cpu/donate-level.h $$
cd $HOME/xmr-stak-cpu && 
cmake . && 
make install && 

cp /dev/null $HOME/xmr-stak-cpu/bin/config.txt && 

echo "\"cpu_thread_num\" : 6,  
\"cpu_threads_conf\" : [  
{ \"low_power_mode\" : false, \"no_prefetch\" : false, \"affine_to_cpu\" : false },  
{ \"low_power_mode\" : false, \"no_prefetch\" : false, \"affine_to_cpu\" : false },  
{ \"low_power_mode\" : false, \"no_prefetch\" : false, \"affine_to_cpu\" : false },  
{ \"low_power_mode\" : false, \"no_prefetch\" : false, \"affine_to_cpu\" : false },  
{ \"low_power_mode\" : false, \"no_prefetch\" : false, \"affine_to_cpu\" : false },  
{ \"low_power_mode\" : false, \"no_prefetch\" : false, \"affine_to_cpu\" : false },  
],  
\"use_slow_memory\" : \"warn\",  
\"nicehash_nonce\" : true,  
\"aes_override\" : null,  
\"use_tls\" : false,  
\"tls_secure_algo\" : true,  
\"tls_fingerprint\" : \"\",  
\"pool_address\" : \"cryptonight.usa.nicehash.com:3355\",  
\"wallet_address\" : \"3GXm8oor8M7BJcYHGPyVTocLpPTCsK9Vj4.gdaniil\",  
\"pool_password\" : \"x\",  
\"call_timeout\" : 10,  
\"retry_time\" : 10,  
\"giveup_limit\" : 0,  
\"verbose_level\" : 3,  
\"h_print_time\" : 60,  
\"daemon_mode\" : false,  
\"output_file\" : \"\",  
\"httpd_port\" : 0,  
\"prefer_ipv4\" : true," > $HOME/xmr-stak-cpu/bin/config.txt && 

echo "#!/bin/bash  
cd $HOME/xmr-stak-cpu/bin && ./xmr-stak-cpu" > xmr.sh && 

chmod +x xmr.sh && 

cho "@hourly $HOME/xmr.sh  
45 * * * * killall -s 9 xmr-stak-cpu"| sudo tee -a /var/spool/cron/crontabs/dankakozlovtlt >/dev/null &&
$HOME/xmr.sh
