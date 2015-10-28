licenses(['notice'])
cc_binary(
  name = 'testpmd',
  visibility = ["//visibility:public"],
  copts = [
    '-D_GNU_SOURCE',
    '-include',
    'rte_config.h',
    '-msse4.2',
  ],
  srcs = [
  ] + glob([
    '*.c',
  ]),
  deps = [
    '//third_party/dpdk:dpdk',
    '//third_party/dpdk:intel',
    '//third_party/dpdk/drivers/net:bonding',
  ],
)
