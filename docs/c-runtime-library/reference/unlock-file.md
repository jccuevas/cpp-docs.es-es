---
title: _unlock_file
ms.date: 11/04/2016
api_name:
- _unlock_file
api_location:
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
- api-ms-win-crt-filesystem-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _unlock_file
- unlock_file
helpviewer_keywords:
- files [C++], unlocking
- unlock_file function
- _unlock_file function
- unlocking files
ms.assetid: cf380a51-6d3a-4f38-bd64-2d4fb57b4369
ms.openlocfilehash: 2983408f066ea00c0b7ab111d9a6349700ecaece
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957475"
---
# <a name="_unlock_file"></a>_unlock_file

Desbloquea un archivo para que otros procesos puedan acceder a él.

## <a name="syntax"></a>Sintaxis

```C
void _unlock_file(
   FILE* file
);
```

### <a name="parameters"></a>Parámetros

*file*<br/>
Identificador de archivo.

## <a name="remarks"></a>Comentarios

La función **_unlock_file** desbloquea el archivo especificado por el *archivo*. El desbloqueo de un archivo permite que otros procesos accedan a él. No se debe llamar a esta función a menos que se haya llamado previamente a **_lock_file** en el puntero de *archivo* . Llamar a **_unlock_file** en un archivo que no está bloqueado puede producir un interbloqueo. A modo de ejemplo, vea [_lock_file](lock-file.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_unlock_file**|\<stdio.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_lock_file](lock-file.md)<br/>
