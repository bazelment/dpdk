licenses(['notice'])

CFLAGS = [
  # Make sure cpuflags is implicitly included.
  '-include',
  'generated_rte_cpuflags.h',
  # Make sure rte_config.h is implicitly included
  '-include',
  'rte_config.h',
  '-march=native',
]

cc_library(
  name = 'core-includes',
  includes = [
    'librte_eal/common',
    'librte_eal/common/include',
    'librte_eal/common/include/arch/x86',
    'librte_eal/linuxapp/eal/include',
    'librte_malloc',
    'librte_mempool',
    'librte_net',
    'librte_ring',
  ],
  hdrs = glob([
    'librte_eal/common/*.h',
    'librte_eal/common/include/*.h',
    'librte_eal/common/include/generic/*.h',
    'librte_eal/common/include/arch/x86/*.h',
    'librte_eal/linuxapp/eal/*.h',
    'librte_eal/linuxapp/eal/include/*.h',
    'librte_eal/linuxapp/eal/include/exec-env/*.h',
    'librte_malloc/*.h',
    'librte_mempool/*.h',
    'librte_net/*.h',
    'librte_ring/*.h',
  ]),
  deps = [
    '//third_party/dpdk:build_config',
  ]
)

cc_library(
  name = 'compat',
  includes = [
    'librte_compat'
  ],
  hdrs = glob([
    'librte_compat/*.h',
  ]),
)

cc_library(
  name = 'acl',
  visibility = ["//visibility:public"],
  copts = CFLAGS,
  includes = [
    'librte_acl',
  ],
  hdrs = glob([
    'librte_acl/*.h',
  ]),
  srcs = glob([
    'librte_acl/*.c',
  ], exclude=[
    'librte_acl/acl_run_neon.c',  # for ARM
  ]),
  deps = [
    ':core-includes',
  ],
)

cc_library(
  name = 'cfgfile',
  visibility = ["//visibility:public"],
  copts = CFLAGS,
  includes = [
    'librte_cfgfile',
  ],
  hdrs = glob([
    'librte_cfgfile/*.h',
  ]),
  srcs = glob([
    'librte_cfgfile/*.c',
  ]),
  deps = [
    ':core-includes',
    ':eal',
  ],
)

cc_library(
  name = 'cmdline',
  visibility = ["//visibility:public"],
  copts = CFLAGS + [
    '-Wno-unused-result',
    '-D_GNU_SOURCE',
  ],
  includes = [
    'librte_cmdline',
  ],
  hdrs = glob([
    'librte_cmdline/*.h',
  ]),
  srcs = glob([
    'librte_cmdline/*.c',
  ]),
  deps = [
    ':core-includes',
    ':eal',
  ],
)

cc_library(
  name = 'eal',
  visibility = ["//visibility:public"],
  copts = CFLAGS + [
    '-D_GNU_SOURCE',
    '-Wno-unused-result',
  ],
  linkopts = [
    '-pthread',
    '-ldl',
  ],
  includes = [
    'librte_malloc',
    'librte_mempool',
    'librte_ring',
  ],
  hdrs = glob([
    'librte_eal/common/*.h',
    'librte_malloc/*.h',
    'librte_mempool/*.h',
    'librte_ring/*.h',
  ]),
  srcs = [
    'librte_eal/common/eal_common_cpuflags.c',
    'librte_eal/common/eal_common_dev.c',
    'librte_eal/common/eal_common_devargs.c',
    'librte_eal/common/eal_common_errno.c',
    'librte_eal/common/eal_common_hexdump.c',
    'librte_eal/common/eal_common_launch.c',
    'librte_eal/common/eal_common_lcore.c',
    'librte_eal/common/eal_common_log.c',
    'librte_eal/common/eal_common_memory.c',
    'librte_eal/common/eal_common_memzone.c',
    'librte_eal/common/eal_common_options.c',
    'librte_eal/common/eal_common_pci.c',
    'librte_eal/common/eal_common_pci_uio.c',
    'librte_eal/common/eal_common_string_fns.c',
    'librte_eal/common/eal_common_tailqs.c',
    'librte_eal/common/eal_common_timer.c',
    'librte_eal/common/eal_common_thread.c',
    'librte_eal/common/malloc_elem.c',
    'librte_eal/common/malloc_heap.c',
    'librte_eal/common/rte_malloc.c',
    'librte_eal/linuxapp/eal/eal.c',
    'librte_eal/linuxapp/eal/eal_alarm.c',
    'librte_eal/linuxapp/eal/eal_debug.c',
    'librte_eal/linuxapp/eal/eal_hugepage_info.c',
    'librte_eal/linuxapp/eal/eal_interrupts.c',
    'librte_eal/linuxapp/eal/eal_ivshmem.c',
    'librte_eal/linuxapp/eal/eal_lcore.c',
    'librte_eal/linuxapp/eal/eal_log.c',
    'librte_eal/linuxapp/eal/eal_memory.c',
    'librte_eal/linuxapp/eal/eal_pci.c',
    'librte_eal/linuxapp/eal/eal_pci_uio.c',
    'librte_eal/linuxapp/eal/eal_pci_vfio.c',
    'librte_eal/linuxapp/eal/eal_pci_vfio_mp_sync.c',
    'librte_eal/linuxapp/eal/eal_thread.c',
    'librte_eal/linuxapp/eal/eal_timer.c',
    'librte_mempool/rte_mempool.c',
  ] + glob([
    'librte_malloc/*.c',
    'librte_ring/*.c',
  ]),
  deps = [
    ':core-includes',
  ],
)

cc_library(
  name = 'ether',
  visibility = ["//visibility:public"],
  copts = CFLAGS,
  includes = [
    'librte_ether',
  ],
  hdrs = glob([
    'librte_ether/*.h',
  ]),
  srcs = [
    'librte_ether/rte_ethdev.c',
  ],
  deps = [
    ':mbuf',
    ':eal',
  ],
)

cc_library(
  name = 'hash',
  visibility = ["//visibility:public"],
  copts = CFLAGS,
  includes = [
    'librte_hash',
  ],
  hdrs = glob([
    'librte_hash/*.h',
  ]),
  srcs = glob([
    'librte_hash/*.c',
  ]),
  deps = [
    ':core-includes',
    ':compat',
    ':eal',
    ':malloc',
  ],
)

cc_library(
  name = 'ip_frag',
  visibility = ["//visibility:public"],
  copts = CFLAGS,
  includes = [
    'librte_ip_frag',
  ],
  hdrs = glob([
    'librte_ip_frag/*.h',
  ]),
  srcs = glob([
    'librte_ip_frag/*.c',
  ]),
  deps = [
    ':core-includes',
    ':eal',
    ':hash',
    ':malloc',
    ':mbuf',
  ],
)

cc_library(
  name = 'kni',
  visibility = ["//visibility:public"],
  copts = CFLAGS,
  includes = [
    'librte_kni',
  ],
  hdrs = glob([
    'librte_kni/*.h',
  ]),
  srcs = glob([
    'librte_kni/*.c',
  ]),
  deps = [
    ':eal',
    ':ether',
    ':mbuf',
  ],
)

cc_library(
  name = 'kvargs',
  visibility = ["//visibility:public"],
  copts = CFLAGS,
  includes = [
    'librte_kvargs',
  ],
  hdrs = glob([
    'librte_kvargs/*.h',
  ]),

  srcs = [
  ] + glob([
    'librte_kvargs/*.c',
  ]),
  deps = [
    ':eal',
  ],
)

cc_library(
  name = 'lpm',
  visibility = ["//visibility:public"],
  copts = CFLAGS,
  includes = [
    'librte_lpm',
  ],
  hdrs = glob([
    'librte_lpm/*.h',
  ]),
  srcs = glob([
    'librte_lpm/*.c',
  ]),
  deps = [
    ':core-includes',
    ':eal',
    ':malloc',
  ],
)
cc_library(
  name = 'malloc',
  visibility = ["//visibility:public"],
  copts = CFLAGS,
  includes = [
  ],
  hdrs = glob([
  ]),
  srcs = glob([
  ]),
  deps = [
    ':core-includes',
  ],
)

cc_library(
  name = 'mbuf',
  visibility = ["//visibility:public"],
  copts = CFLAGS,
  includes = [
    'librte_mbuf',
  ],
  hdrs = [
    'librte_mbuf/rte_mbuf.h',
  ],
  srcs = [
    'librte_mbuf/rte_mbuf.c',
  ],
  deps = [
    ':eal',
  ],
)

cc_library(
  name = 'net',
  visibility = ["//visibility:public"],
  includes = [
    'librte_net',
  ],
)
