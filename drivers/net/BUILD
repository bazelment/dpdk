licenses(['notice'])

load('//third_party/dpdk:dpdk_cpu.bzl', 'DPDK_CONFIG_CFLAGS')

cc_library(
  name = 'af_packet',
  visibility = ["//visibility:public"],
  copts = DPDK_CONFIG_CFLAGS,
  includes = [
    'af_packet',
  ],
  hdrs = glob([
    'af_packet/*.h',
  ]),
  srcs = glob([
    'af_packet/*.c',
  ]),
  deps = [
    '//third_party/dpdk:dpdk',
    '//third_party/dpdk/lib:kvargs',
  ],
)

cc_library(
  name = 'bonding',
  visibility = ["//visibility:public"],
  copts = DPDK_CONFIG_CFLAGS + [
    '-Wno-uninitialized',
    '-Wno-unused-variable',
  ],
  includes = [
    'bonding',
  ],
  hdrs = glob([
    'bonding/*.h',
  ]),
  srcs = [
  ] + glob([
    'bonding/*.c',
  ]),
  deps = [
    '//third_party/dpdk:dpdk',
    '//third_party/dpdk/lib:kvargs',
  ],
)

# Intel cards
cc_library(
  name = 'e1000',
  visibility = ["//visibility:public"],
  copts = DPDK_CONFIG_CFLAGS + [
    '-Wno-uninitialized',
    '-Wno-unused-variable',
  ],
  includes = [
    'e1000',
  ],
  hdrs = glob([
    'e1000/*.h',
    'e1000/base/*.h',
    'e1000/e1000/*.h',
  ]),
  srcs = [
  ] + glob([
    'e1000/base/*.c',
    'e1000/e1000/e1000_*.c',
  ]),
  deps = [
    '//third_party/dpdk:dpdk',
  ],
)

cc_library(
  name = 'em',
  visibility = ["//visibility:public"],
  copts = DPDK_CONFIG_CFLAGS + [
    '-Wno-uninitialized',
  ],
  srcs = glob([
    'e1000/em_*.c',
  ]),
  deps = [
    ':e1000',
  ],
)

cc_library(
  name = 'i40e',
  visibility = ["//visibility:public"],
  copts = DPDK_CONFIG_CFLAGS + [
    '-DPF_DRIVER',
    '-DVF_DRIVER',
    '-DINTEGRATED_VF',
    '-DX722_SUPPORT',
    '-DX722_A0_SUPPORT',
    '-Wno-unused-variable',
  ],
  includes = [
    'i40e',
  ],
  hdrs = glob([
    'i40e/base/*.h',
    'i40e/*.h',
  ]),
  srcs = glob([
    'i40e/base/*.c',
    'i40e/*.c',
  ]),
  deps = [
    '//third_party/dpdk:dpdk',
  ],
)

cc_library(
  name = 'igb',
  visibility = ["//visibility:public"],
  copts = DPDK_CONFIG_CFLAGS + [
    '-Wno-uninitialized',
  ],
  srcs = glob([
    'e1000/igb_*.c',
  ]),
  deps = [
    ':e1000',
  ],
)

cc_library(
  name = 'ixgbe',
  visibility = ["//visibility:public"],
  copts = DPDK_CONFIG_CFLAGS + [
    '-Wno-unused-result',
    '-Wno-unused-value',
    '-msse4.2',
  ],
  includes = [
    'ixgbe',
  ],
  hdrs = glob([
    'ixgbe/*.h',
    'ixgbe/base/*.h',
  ]),
  srcs = glob([
    'ixgbe/base/*.c',
    'ixgbe/*.c'
  ], exclude=[
    'ixgbe/ixgbe_bypass.c',
    'ixgbe/ixgbe_82599_bypass.c',
  ]),
  deps = [
    '//third_party/dpdk:dpdk',
  ],
)

# For testing
cc_library(
  name = 'null',
  visibility = ["//visibility:public"],
  copts = DPDK_CONFIG_CFLAGS,
  includes = [
    'null',
  ],
  hdrs = glob([
    'null/*.h',
  ]),
  srcs = glob([
    'null/*.c',
  ]),
  deps = [
    '//third_party/dpdk:dpdk',
    '//third_party/dpdk/lib:kvargs',
  ],
)

cc_library(
  name = 'ring',
  visibility = ["//visibility:public"],
  copts = DPDK_CONFIG_CFLAGS,
  includes = [
    'ring',
  ],
  hdrs = glob([
    'ring/*.h',
  ]),
  srcs = glob([
    'ring/*.c',
  ]),
  deps = [
    '//third_party/dpdk:dpdk',
    '//third_party/dpdk/lib:kvargs',
  ],
)

# For VM like qemu

cc_library(
  name = 'virtio',
  visibility = ["//visibility:public"],
  copts = DPDK_CONFIG_CFLAGS,
  includes = [
    'virtio',
  ],
  hdrs = glob([
    'virtio/*.h',
  ]),
  srcs = glob([
    'virtio/*.c',
  ]),
  deps = [
    '//third_party/dpdk:dpdk',
    '//third_party/dpdk/lib:kvargs',
  ],
)
