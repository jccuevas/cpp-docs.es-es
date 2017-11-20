---
title: _rmdir, _wrmdir | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wrmdir
- _rmdir
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- trmdir
- _trmdir
- wrmdir
- _rmdir
- _wrmdir
dev_langs: C++
helpviewer_keywords:
- _rmdir function
- directories [C++], deleting
- rmdir function
- directories [C++], removing
- trmdir function
- _trmdir function
- _wrmdir function
- wrmdir function
ms.assetid: 652c2a5a-b0ac-4493-864e-1edf484333c5
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9770c84f2035687ca1ce9a7e3ae1d1e34df7d5d4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="rmdir-wrmdir"></a>_rmdir, _wrmdir
Elimina un directorio.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      int _rmdir(  
   const char *dirname   
);  
int _wrmdir(  
   const wchar_t *dirname   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dirname`  
 Ruta de acceso del directorio que se va a quitar.  
  
## <a name="return-value"></a>Valor devuelto  
 Cada una de estas funciones devuelve 0 si el directorio se elimina correctamente. Un valor devuelto de -1 indica un error y `errno` se establece en uno de los siguientes valores:  
  
 **ENOTEMPTY**  
 La ruta de acceso especificada no es un directorio, el directorio no está vacío o el directorio es el directorio de trabajo actual o el directorio raíz.  
  
 `ENOENT`  
 La ruta de acceso no es válida.  
  
 **EACCES**  
 Un programa tiene un identificador abierto en el directorio.  
  
 Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 La función `_rmdir` elimina el directorio especificado por `dirname`. El directorio debe estar vacío y no debe ser el directorio de trabajo actual ni el directorio raíz.  
  
 `_wrmdir` es una versión con caracteres anchos de `_rmdir`; el argumento `dirname` para `_wrmdir` es una cadena de caracteres anchos. Por lo demás, `_wrmdir` y `_rmdir` se comportan de forma idéntica.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_trmdir`|`_rmdir`|`_rmdir`|`_wrmdir`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_rmdir`|\<direct.h>|  
|`_wrmdir`|\<direct.h> o \<wchar.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [_mkdir](../../c-runtime-library/reference/mkdir-wmkdir.md).  
  
## <a name="see-also"></a>Vea también  
 [Control de directorio](../../c-runtime-library/directory-control.md)   
 [_chdir, _wchdir](../../c-runtime-library/reference/chdir-wchdir.md)   
 [_mkdir, _wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)