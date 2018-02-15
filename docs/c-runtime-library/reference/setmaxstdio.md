---
title: _setmaxstdio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _setmaxstdio
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
- setmaxstdio
- _setmaxstdio
dev_langs:
- C++
helpviewer_keywords:
- maximum open files
- _setmaxstdio function
- setmaxstdio function
- open files, maximum
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5317437202cef423759ac850aab2360892521746
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="setmaxstdio"></a>_setmaxstdio
Establece un máximo para el número de archivos abiertos simultáneamente en el nivel de `stdio`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _setmaxstdio(  
   int newmax   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `newmax`  
 Nuevo máximo para el número de archivos abiertos simultáneamente en el nivel de `stdio`.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `newmax` si se realiza correctamente; en caso contrario de -1.  
  
 Si `newmax` es menor que `_IOB_ENTRIES` o mayor que el número máximo de controladores disponibles en el sistema operativo, se invoca al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve -1 y establece `errno` en `EINVAL`.  
  
 Para obtener información sobre estos y otros códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 La función `_setmaxstdio` cambia el valor máximo del número de archivos que se pueden abrir simultáneamente en el nivel de `stdio`.  
  
 La E/S en tiempo de ejecución de C ahora admite muchos más archivos abiertos en las plataformas de Win32 que en las versiones anteriores. En el [nivel de lowio](../../c-runtime-library/low-level-i-o.md) se pueden abrir simultáneamente hasta 2048 archivos (es decir, se abren y se obtiene acceso a ellos mediante las familias `_open`, `_read`, `_write`, etc. de las funciones de E/S). En el [nivel de stdio](../../c-runtime-library/stream-i-o.md) se pueden abrir simultáneamente hasta 512 archivos (es decir, se abren y se obtiene acceso a ellos mediante las familias `fopen`, `fgetc`, `fputc`, etc. de las funciones). El límite de 512 archivos abiertos en el nivel de `stdio` se puede aumentar hasta un máximo de 2048 mediante la función `_setmaxstdio`.  
  
 Dado que las funciones de nivel `stdio` (como `fopen`) se crean a partir de las funciones `lowio`, el máximo de 2048 archivos es un límite superior para el número de archivos abiertos simultáneamente a los que se obtiene acceso a través de la biblioteca de tiempo de ejecución de C.  
  
> [!NOTE]
>  Este límite superior puede exceder la compatibilidad de ciertas plataformas y configuraciones de Win32.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_setmaxstdio`|\<stdio.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
 Vea [_getmaxstdio](../../c-runtime-library/reference/getmaxstdio.md) para obtener un ejemplo del uso de `_setmaxstdio`.  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)