licenses(['notice'])
cc_binary(
  name = 'l2fwd',
  copts = [
    '-include',
    'rte_config.h',
  ],
  srcs = [
    'main.c',
  ],
  deps = [
    '//third_party/dpdk',
    '//third_party/dpdk:intel',
  ],
)
