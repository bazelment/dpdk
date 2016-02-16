licenses(['notice'])
cc_binary(
  name = 'testpmd',
  visibility = ["//visibility:public"],
  copts = [
    '-D_GNU_SOURCE',
    '-include',
    'rte_config.h',
    '-msse4.2',
    # This is needed because we now get the defines from dpdk, which
    # enabled AVX2, so that certain code that depends on this
    # feature(like memcpy) requires the compiler to optimize at
    # certain level to work correctly.
    '-march=native',
  ],
  srcs = glob([
    '*.h',
    '*.c',
  ]),
  deps = [
    '//third_party/dpdk:dpdk',
    '//third_party/dpdk:intel',
    '//third_party/dpdk/drivers/net:bonding',
  ],
)
