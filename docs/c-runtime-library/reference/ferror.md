---
title: ferror | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- ferror
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
- ferror
dev_langs:
- C++
helpviewer_keywords:
- ferror function
- streams, testing for errors
- errors [C++], testing for stream
ms.assetid: 528a34bc-f2aa-4c3f-b89a-5b148e6864f7
caps.latest.revision: 13
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
ms.openlocfilehash: 1828b9316cf29d953a6db8f8a6c11b5a3a08c346
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="ferror"></a>ferror
Pruebas de error en una secuencia.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int ferror(   
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `stream`  
 Puntero a la estructura `FILE` .  
  
## <a name="return-value"></a>Valor devuelto  
 Si no se ha producido ningún error en `stream`, `ferror` devuelve 0. De lo contrario, devuelve un valor distinto de cero. Si la secuencia es `NULL`, `ferror` invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece `errno` en `EINVAL` y devuelve 0.  
  
 Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.  
  
## <a name="remarks"></a>Comentarios  
 La rutina `ferror` (que se implementa como función y como macro) realiza pruebas de error de lectura o escritura en el archivo asociado a `stream`. Si se ha producido un error, el indicador de error de la secuencia permanece establecido hasta que la secuencia se cierre o rebobine o hasta que se llame a `clearerr` en ella.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`ferror`|\<stdio.h>|  
  
 Para obtener información adicional de compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
 Consulte el ejemplo de [feof](../../c-runtime-library/reference/feof.md).  
  
## <a name="see-also"></a>Vea también  
 [Control de errores](../../c-runtime-library/error-handling-crt.md)   
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [clearerr](../../c-runtime-library/reference/clearerr.md)   
 [_eof](../../c-runtime-library/reference/eof.md)   
 [feof](../../c-runtime-library/reference/feof.md)   
 [fopen, _wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [perror, _wperror](../../c-runtime-library/reference/perror-wperror.md)
