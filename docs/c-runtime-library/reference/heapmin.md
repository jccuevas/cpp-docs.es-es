---
title: _heapmin | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _heapmin
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _heapmin
- heapmin
dev_langs:
- C++
helpviewer_keywords:
- heap memory
- minimizing heaps
- memory, releasing
- heaps, releasing unused memory
- _heapmin function
- heapmin function
ms.assetid: c0bccdf6-2d14-4d7b-a7ff-d6a17bdb410f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ec73905c6361d025b9f29c8cf4543ed200a4abbf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="heapmin"></a>_heapmin

Libera la memoria del montón no utilizada al sistema operativo.

## <a name="syntax"></a>Sintaxis

```C
int _heapmin( void );
```

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, **_heapmin** devuelve 0; en caso contrario, la función devuelve -1 y establece **errno** a **ENOSYS**.

Para obtener más información sobre este y otros códigos de retorno, consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **_heapmin** función minimiza el montón, liberar memoria del montón no utilizado en el sistema operativo. Si el sistema operativo no admite **_heapmin**(por ejemplo, Windows 98), la función devuelve -1 y establece **errno** a **ENOSYS**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_heapmin**|\<malloc.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[free](free.md)<br/>
[_heapadd](../../c-runtime-library/heapadd.md)<br/>
[_heapchk](heapchk.md)<br/>
[_heapset](../../c-runtime-library/heapset.md)<br/>
[_heapwalk](heapwalk.md)<br/>
[malloc](malloc.md)<br/>
