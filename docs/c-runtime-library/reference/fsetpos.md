---
title: fsetpos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- fsetpos
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
- fsetpos
dev_langs:
- C++
helpviewer_keywords:
- streams, setting position indicators
- fsetpos function
ms.assetid: 6d19ff48-1a2b-47b3-9f23-ed0a47b5a46e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 483cf151374c1c3a03e53e49ce67a00a148406fd
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="fsetpos"></a>fsetpos
Establece el indicador de posición de secuencia.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int fsetpos(   
   FILE *stream,  
   const fpos_t *pos   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `stream`  
 Puntero a la estructura `FILE` .  
  
 `pos`  
 Almacenamiento del indicador de posición.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, `fsetpos` devuelve 0. En caso de error, la función devuelve un valor distinto de cero y establece `errno` en una de las siguientes constantes de manifiesto (que se definen en ERRNO.H): `EBADF`, que significa que el archivo no está accesible o que el objeto que apunta a `stream` no es una estructura de archivo válida; o `EINVAL`, que significa que se ha pasado un valor no válido para `stream` o `pos`. Si se pasa un parámetro no válido, estas funciones invocan al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  
  
 Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de retorno.  
  
## <a name="remarks"></a>Comentarios  
 El `fsetpos` función establece el indicador de posición de archivo para `stream` en el valor de `pos`, que se obtiene en una llamada anterior a `fgetpos` en `stream`. La función borra el indicador de fin de archivo y deshace los efectos de [ungetc](../../c-runtime-library/reference/ungetc-ungetwc.md) en `stream`. Después de llamar a `fsetpos`, puede que la siguiente operación en `stream` sea de entrada o de salida.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`fsetpos`|\<stdio.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
 Consulte el ejemplo de [fgetpos](../../c-runtime-library/reference/fgetpos.md).  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fgetpos](../../c-runtime-library/reference/fgetpos.md)