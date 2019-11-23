1，根据源ip和目标ip进行聚合
2，威胁等级列表
(高危，中危险，低危)
enrichments:threat_name_level
3，威胁名称Top10 [和4对应]
enrichments:threat_name
4，威胁类型top 10 【和3对应】
enrichments:threat_type
5，enrichments:geo:ip_src_addr:country_cn 发起方国家Top10
6,enrichments:direction 【方向】

mapping {
    ip_src_addr
    ip_dst_addr
    enrichments:geo:ip_src_addr:country_cn
    enrichments:geo:ip_dst_addr:country_cn
    enrichments:ip_src_addr:asset_name
    enrichments:ip_dst_addr:asset_name
    enrichments:ip_src_addr:asset_type
    enrichments:ip_dst_addr:asset_type
    enrichments:direction
    enrichments:geo:ip_src_addr:asset_group
    enrichments:geo:ip_dst_addr:asset_group
    enrichments:ip_dst_addr_asset_id
    enrichments:ip_src_addr_asset_id
    timestamp:
    period: 
        threat_type_aggs_nest: [
            enrichments:threat_type_level:
            enrichments:threat_type:
            threat_type_num: 
        ],
        thereat_name_aggs_nest: [
            enrichments:threat_name_level:
            enrichments:threat_name:
            threat_name_num: 
        ]
   
}
