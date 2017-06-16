licenses(['notice'])

cc_binary(
  name = 'test',
  visibility = ["//visibility:public"],
  copts = [
    '-include',
    'rte_config.h',
    '-march=native',
  ],
  srcs = [
    'test.h',
    'packet_burst_generator.h',
    'packet_burst_generator.c',
    'commands.c',
    'test.c',
    'process.h',
    'test_mp_secondary.c',
    #'test_pci.c',
    # all test cases
    'test_pmd_perf.c',
    'test_acl.h',
    'test_acl.c',
    'test_mbuf.c',
  ],
  deps = [
    '//third_party/dpdk',
    '//third_party/dpdk/lib:timer',
    '//third_party/dpdk/lib:lpm',
  ],
)
