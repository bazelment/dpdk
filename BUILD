# This file is the top level BUILD file to use DPDK as a library when
# building with bazel. Most application libraries should just depend
# on dpdk library, which is essentially the core collection of DPDK
# libraries. A cc_binary that uses DPDK should put 'intel' into the
# deps if it wants to use Intel NIC, or any other PMD defined in
# drivers/net/BUILD.
licenses(['notice'])

cc_library(
  name = 'build_config',
  visibility = [":__subpackages__"],
  hdrs = [
    'linux-k8/rte_config.h',
    'linux-k8/generated_rte_cpuflags.h',
  ],
  defines = [
    'RTE_MAX_QUEUES_PER_PORT=256',
  ],
  includes = [
    'linux-k8',
    'drivers/net/ring',
  ]
)

cc_library(
  name = 'dpdk',
  visibility = ["//visibility:public"],
  deps = [
    '//third_party/dpdk/lib:acl',
    '//third_party/dpdk/lib:cmdline',
    '//third_party/dpdk/lib:eal',
    '//third_party/dpdk/lib:ether',
    '//third_party/dpdk/lib:mbuf',
    '//third_party/dpdk/lib:net',
  ],
)

# Intel PMD drivers
cc_library(
  name = 'intel',
  visibility = ["//visibility:public"],
  deps = [
    '//third_party/dpdk/drivers/net:e1000',
    '//third_party/dpdk/drivers/net:em',
    '//third_party/dpdk/drivers/net:i40e',
    '//third_party/dpdk/drivers/net:igb',
    '//third_party/dpdk/drivers/net:ixgbe',
  ],
)
