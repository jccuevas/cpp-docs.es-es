---
title: _open_osfhandle | Microsoft Docs
ms.custom: ''
ms.date: 12/12/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _open_osfhandle
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _open_osfhandle
- open_osfhandle
dev_langs:
- C++
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 270b17ce72ece85687c23678908e10bc1dcc3764
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="openosfhandle"></a>_open_osfhandle

Asocia un descriptor de archivo en tiempo de ejecución de C al identificador de archivo del sistema operativo existente.

## <a name="syntax"></a>Sintaxis

```cpp
int _open_osfhandle (
   intptr_t osfhandle,
   int flags
);
```

### <a name="parameters"></a>Parámetros

*osfhandle*<br/>
Identificador de archivo del sistema operativo.

*flags*<br/>
Tipos de operaciones permitidas.

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, **_open_osfhandle** devuelve un descriptor de archivo de tiempo de ejecución de C. En caso contrario, devuelve -1.

## <a name="remarks"></a>Comentarios

El **_open_osfhandle** función asigna un descriptor de archivo de tiempo de ejecución de C y lo asocia con el identificador de archivo del sistema operativo especificado por *osfhandle*. El *marcas* argumento es una expresión de entero formada por una o varias de las constantes de manifiesto definidas en Fcntl.h. Cuando se usan dos o más constantes del manifiesto para formar el *marcas* argumento, estas constantes se combinan con el operador OR bit a bit ( **&#124;** ).

Fcntl.h define las constantes de manifiesto siguientes:

**\_O\_ANEXADO** coloca un puntero de archivo al final del archivo antes de cada operación de escritura.

**\_O\_RDONLY** abre el archivo de solo lectura.

**\_O\_texto** abre el archivo en modo de texto (traducido).

**\_O\_WTEXT** abre el archivo en modo Unicode (UTF-16 traducidos).

Para cerrar un archivo abierto con **_open_osfhandle**, llame a [ \_cerrar](close.md). También se cierra el identificador de archivo del sistema operativo subyacente mediante una llamada a **_close**, por lo que no es necesario llamar a la función de Win32 **CloseHandle** en el identificador original. Si el descriptor de archivo pertenece a un **archivo &#42;**  secuencia, a continuación, llamar a [fclose](fclose-fcloseall.md) en ese **archivo &#42;**  secuencia también cierra el descriptor de archivo y la identificador subyacente. En este caso, no llame a **_close** en el descriptor de archivo.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
