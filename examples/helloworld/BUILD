licenses(['notice'])
cc_binary(
  name = 'helloworld',
  visibility = ["//visibility:public"],
  copts = [
    '-include',
    'rte_config.h',
  ],
  srcs = [
    'main.c',
  ],
  deps = [
    '//third_party/dpdk',
  ],
)
