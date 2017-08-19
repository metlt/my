sudo apt install libmicrohttpd-dev libssl-dev cmake build-essential libhwloc-dev

https://github.com/fireice-uk/xmr-stak-cpu

"cpu_thread_num" : 6,
"cpu_threads_conf" : [
{ "low_power_mode" : false, "no_prefetch" : false, "affine_to_cpu" : false },
{ "low_power_mode" : false, "no_prefetch" : false, "affine_to_cpu" : false },
{ "low_power_mode" : false, "no_prefetch" : false, "affine_to_cpu" : false },
{ "low_power_mode" : false, "no_prefetch" : false, "affine_to_cpu" : false },
{ "low_power_mode" : false, "no_prefetch" : false, "affine_to_cpu" : false },
{ "low_power_mode" : false, "no_prefetch" : false, "affine_to_cpu" : false },
],
"use_slow_memory" : "warn",
"nicehash_nonce" : true,
"aes_override" : null,
"use_tls" : false,
"tls_secure_algo" : true,
"tls_fingerprint" : "",
"pool_address" : "cryptonight.usa.nicehash.com:3355",
"wallet_address" : "3GXm8oor8M7BJcYHGPyVTocLpPTCsK9Vj4.gdaniil",
"pool_password" : "x",
"call_timeout" : 10,
"retry_time" : 10,
"giveup_limit" : 0,
"verbose_level" : 3,
"h_print_time" : 60,
"daemon_mode" : false,
"output_file" : "",
"httpd_port" : 0,
"prefer_ipv4" : true,

Создать файл xmr.sh
#!/bin/bash
cd $HOME/xmr-stak-cpu/bin && ./xmr-stak-cpu

chmod +x xmr.sh

@hourly $HOME/xmr.sh
45 * * * * killall -s 9 xmr-stak-cpu
