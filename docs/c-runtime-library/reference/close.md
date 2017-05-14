---
title: _close | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _close
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
- _close
dev_langs:
- C++
helpviewer_keywords:
- _close function
- close function
- files [C++], closing
ms.assetid: 4708a329-8acf-4cd9-b7b0-a952e1897247
caps.latest.revision: 12
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 9dab323afc6c70e81592119e0cec2775c239d87f
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="close"></a>_close
Cierra un archivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _close(   
   int fd   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `fd`  
 Descriptor de archivo que hace referencia al archivo abierto.  
  
## <a name="return-value"></a>Valor devuelto  
 `_close` devuelve 0 si la secuencia se ha cerrado correctamente. Un valor devuelto de -1 indica un error.  
  
## <a name="remarks"></a>Comentarios  
 La función `_close` cierra el archivo asociado a `fd`.  
  
 El descriptor de archivo y el identificador de archivos del sistema operativo subyacente se cierran. Por lo tanto, no es necesario llamar a `CloseHandle` si el archivo se ha abierto originalmente mediante la función `CreateFile` de Win32 y se ha convertido en un descriptor de archivo mediante `_open_osfhandle`.  
  
 Esta función valida sus parámetros. Si `fd` es un descriptor de archivo incorrecto, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, las funciones devuelven -1 y `errno` se establece en `EBADF`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|-------------|---------------------|---------------------|  
|`_close`|\<io.h>|\<errno.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="example"></a>Ejemplo  
 Consulte el ejemplo de [_open](../../c-runtime-library/reference/open-wopen.md).  
  
## <a name="see-also"></a>Vea también  
 [E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)   
 [_chsize](../../c-runtime-library/reference/chsize.md)   
 [_creat, _wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [_dup, _dup2](../../c-runtime-library/reference/dup-dup2.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_unlink, _wunlink](../../c-runtime-library/reference/unlink-wunlink.md)
