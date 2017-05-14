---
title: _chsize_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _chsize_s
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
- chsize_s
- _chsize_s
dev_langs:
- C++
helpviewer_keywords:
- files [C++], changing size
- chsize_s function
- _chsize_s function
ms.assetid: d88d2e94-6e3b-42a5-8631-16ac4d82fa38
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: eb8292d70a77a5901c710349d6912e46cfda8f63
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="chsizes"></a>_chsize_s
Cambia el tamaño de un archivo. Se trata de una versión de [_chsize](../../c-runtime-library/reference/chsize.md) con mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
errno_t _chsize_s(   
   int fd,  
   __int64 size   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `fd`  
 Descriptor de archivo que hace referencia a un archivo abierto.  
  
 `size`  
 Nueva longitud del archivo en bytes.  
  
## <a name="return-value"></a>Valor devuelto  
 `_chsize_s` devuelve el valor 0 si el tamaño del archivo se modifica correctamente. Un valor devuelto distinto de cero indica un error: el valor de devuelto es `EACCES` si el archivo especificado está bloqueado contra el acceso, `EBADF` si el archivo especificado es de solo lectura o el descriptor no es válido, `ENOSPC` si no queda espacio en el dispositivo, o `EINVAL` si el tamaño es menor que cero. `errno` se establece en el mismo valor.  
  
 Para obtener más información sobre estos y otros códigos de retorno, consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 La función `_chsize_s` amplía o trunca el archivo asociado a `fd` según la longitud que `size` especifique. El archivo debe estar abierto en un modo que permita escritura. Si el archivo se amplía, se anexan caracteres nulos ("\0"). Si el archivo se trunca, se pierden todos los datos desde el final del archivo abreviado hasta la longitud original del archivo.  
  
 `_chsize_s` toma un entero de 64 bits como tamaño de archivo y, por lo tanto, puede controlar tamaños de archivo de más de 4 GB. `_chsize` se limita a los tamaños de archivo de 32 bits.  
  
 Esta función valida sus parámetros. Si `fd` no es un descriptor de archivo válido o el tamaño es menor que cero, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|-------------|---------------------|---------------------|  
|`_chsize_s`|\<io.h>|\<errno.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="see-also"></a>Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [_chsize](../../c-runtime-library/reference/chsize.md)   
 [_close](../../c-runtime-library/reference/close.md)   
 [_creat, _wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)
