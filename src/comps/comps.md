
定义了一些继承uvm_component的virtual class

- uvm_test, uvm_env, uvm_scoreboard, uvm_monitor
    - containers
    - factory (macro `uvm_component_abstract_utils`)
- agent
    - is_active默认为UVM_ACTIVE
    - 重载uvm_component的build_phase, 从resource_pool中检索对is_active的配置
- driver
    - pull, 通过seq_item_port主动向sequencer请求transaction, 也可以发送RSP.
    - `uvm_seq_item_pull_port #(REQ, RSP) seq_item_port;`
    - `uvm_analysis_port #(RSP) rsp_port;`
    - factory (macro `uvm_component_param_utils`)
- push_driver
    - push, 被动接收transaction
    - `uvm_blocking_put_imp #(REQ, uvm_push_driver #(REQ,RSP)) req_export;`
    - `uvm_analysis_port #(RSP) rsp_port;`
    - virtual put task必须被重载

