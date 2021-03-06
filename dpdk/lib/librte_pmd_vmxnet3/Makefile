#   BSD LICENSE
# 
#   Copyright(c) 2010-2014 Intel Corporation. All rights reserved.
#   All rights reserved.
# 
#   Redistribution and use in source and binary forms, with or without
#   modification, are permitted provided that the following conditions
#   are met:
# 
#     * Redistributions of source code must retain the above copyright
#       notice, this list of conditions and the following disclaimer.
#     * Redistributions in binary form must reproduce the above copyright
#       notice, this list of conditions and the following disclaimer in
#       the documentation and/or other materials provided with the
#       distribution.
#     * Neither the name of Intel Corporation nor the names of its
#       contributors may be used to endorse or promote products derived
#       from this software without specific prior written permission.
# 
#   THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
#   "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
#   LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
#   A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
#   OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
#   SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
#   LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
#   DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
#   THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
#   (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
#   OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

include $(RTE_SDK)/mk/rte.vars.mk

#
# library name
#
LIB = librte_pmd_vmxnet3_uio.a

CFLAGS += -O3
CFLAGS += $(WERROR_FLAGS)

ifeq ($(CC), icc)
#
# CFLAGS for icc
#
CFLAGS_LAD = -wd174 -wd593 -wd869 -wd981 -wd2259
else 
#
# CFLAGS for gcc
#
ifneq ($(shell test $(GCC_MAJOR_VERSION) -le 4 -a $(GCC_MINOR_VERSION) -le 3 && echo 1), 1)
CFLAGS     += -Wno-deprecated
endif
CFLAGS_LAD = -Wno-unused-parameter -Wno-unused-value
CFLAGS_LAD += -Wno-strict-aliasing -Wno-format-extra-args

endif

VPATH += $(RTE_SDK)/lib/librte_pmd_vmxnet3/vmxnet3

#
# all source are stored in SRCS-y
#
SRCS-$(CONFIG_RTE_LIBRTE_VMXNET3_PMD) += vmxnet3_rxtx.c
SRCS-$(CONFIG_RTE_LIBRTE_VMXNET3_PMD) += vmxnet3_ethdev.c

# this lib depends upon:
DEPDIRS-$(CONFIG_RTE_LIBRTE_VMXNET3_PMD) += lib/librte_eal lib/librte_ether
DEPDIRS-$(CONFIG_RTE_LIBRTE_VMXNET3_PMD) += lib/librte_mempool lib/librte_mbuf
DEPDIRS-$(CONFIG_RTE_LIBRTE_VMXNET3_PMD) += lib/librte_net lib/librte_malloc

include $(RTE_SDK)/mk/rte.lib.mk
