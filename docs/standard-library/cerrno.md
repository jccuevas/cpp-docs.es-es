---
title: '&lt;cerrno&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cerrno>
helpviewer_keywords:
- cerrno header
ms.assetid: c618f95c-ad4b-4a6f-825b-8727322ec77a
ms.openlocfilehash: 1186a1e3c58c34de53f7a9835eaf9fd188593301
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455497"
---
# <a name="ltcerrnogt"></a>&lt;cerrno&gt;

Incluye el encabezado \<de la biblioteca estándar de C errno. h > y agrega los nombres `std` asociados al espacio de nombres. Incluir este encabezado garantiza que los nombres declarados mediante vinculación externa en el encabezado de la biblioteca estándar `std` de C se declaran en el espacio de nombres.

## <a name="syntax"></a>Sintaxis

```cpp
#include <cerrno>
```

## <a name="macros"></a>Macros

```cpp
#define errno
#define E2BIG
#define EACCES
#define EADDRINUSE
#define EADDRNOTAVAIL
#define EAFNOSUPPORT
#define EAGAIN
#define EALREADY
#define EBADF
#define EBADMSG
#define EBUSY
#define ECANCELED
#define ECHILD
#define ECONNABORTED
#define ECONNREFUSED
#define ECONNRESET
#define EDEADLK
#define EDESTADDRREQ
#define EDOM
#define EEXIST
#define EFAULT
#define EFBIG
#define EHOSTUNREACH
#define EIDRM
#define EILSEQ
#define EINPROGRESS
#define EINTR
#define EINVAL
#define EIO
#define EISCONN
#define EISDIR
#define ELOOP
#define EMFILE
#define EMLINK
#define EMSGSIZE
#define ENAMETOOLONG
#define ENETDOWN
#define ENETRESET
#define ENETUNREACH
#define ENFILE
#define ENOBUFS
#define ENODATA
#define ENODEV
#define ENOENT
#define ENOEXEC
#define ENOLCK
#define ENOLINK
#define ENOMEM
#define ENOMSG
#define ENOPROTOOPT
#define ENOSPC
#define ENOSR
#define ENOSTR
#define ENOSYS
#define ENOTCONN
#define ENOTDIR
#define ENOTEMPTY
#define ENOTRECOVERABLE
#define ENOTSOCK
#define ENOTSUP
#define ENOTTY
#define ENXIO
#define EOPNOTSUPP
#define EOVERFLOW
#define EOWNERDEAD
#define EPERM
#define EPIPE
#define EPROTO
#define EPROTONOSUPPORT
#define EPROTOTYPE
#define ERANGE
#define EROFS
#define ESPIPE
#define ESRCH
#define ETIME
#define ETIMEDOUT
#define ETXTBSY
#define EWOULDBLOCK
#define EXDEV
```

### <a name="remarks"></a>Comentarios

Las macros se definen en el estándar POSIX.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Información general sobre la biblioteca estándar de C++](../standard-library/cpp-standard-library-overview.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
