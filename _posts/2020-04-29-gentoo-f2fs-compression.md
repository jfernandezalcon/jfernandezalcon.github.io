---
layout: post
title:  "Running F2FS with compression in Gentoo"
date:   2020-04-29 21:04
categories: gentoo
author: Blackmagic
---

Creating the filesystem:

```bash
 sudo ./mkfs.f2fs -l gentoo -t 0 -O encrypt,compression,extra_attr /dev/nvme0n1p4
```

Edit /etc/fstab:

```bash
/dev/nvme0n1p4      /gentoo     f2fs    noauto,noatime,compress_algorithm=lz4 0 1
rw,noatime,background_gc=on,discard,inline_data,extent_cache,active_logs=6 0 0
```

The list of features that can be passed to the -O argument can be found here:
[F2FS filesystem features](https://git.kernel.org/pub/scm/linux/kernel/git/jaegeuk/f2fs-tools.git/tree/include/f2fs_fs.h#n1361)

```
#define INIT_FEATURE_TABLE						\
struct feature feature_table[] = {					\
	{ "encrypt",			F2FS_FEATURE_ENCRYPT },		\
	{ "extra_attr",			F2FS_FEATURE_EXTRA_ATTR },	\
	{ "project_quota",		F2FS_FEATURE_PRJQUOTA },	\
	{ "inode_checksum",		F2FS_FEATURE_INODE_CHKSUM },	\
	{ "flexible_inline_xattr",	F2FS_FEATURE_FLEXIBLE_INLINE_XATTR },\
	{ "quota",			F2FS_FEATURE_QUOTA_INO },	\
	{ "inode_crtime",		F2FS_FEATURE_INODE_CRTIME },	\
	{ "lost_found",			F2FS_FEATURE_LOST_FOUND },	\
	{ "verity",			F2FS_FEATURE_VERITY },	/* reserved */ \
	{ "sb_checksum",		F2FS_FEATURE_SB_CHKSUM },	\
	{ "casefold",			F2FS_FEATURE_CASEFOLD },	\
	{ "compression",		F2FS_FEATURE_COMPRESSION },	\
	{ NULL,				0x0},				\
};
```
