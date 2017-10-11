---
title: _open_osfhandle | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 8d214df5d1e1cd3a48336723cecbf530402eafe3
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="openosfhandle"></a>_open_osfhandle
Asocia un descriptor de archivo en tiempo de ejecución de C al identificador de archivo del sistema operativo existente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      int _open_osfhandle (  
   intptr_t osfhandle,  
   int flags   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `osfhandle`  
 Identificador de archivo del sistema operativo.  
  
 `flags`  
 Tipos de operaciones permitidas.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, `_open_osfhandle` devuelve un descriptor de archivo en tiempo de ejecución de C. En caso contrario, devuelve -1.  
  
## <a name="remarks"></a>Comentarios  
 La función `_open_osfhandle` asigna un descriptor de archivo en tiempo de ejecución de C y lo asocia al identificador de archivo del sistema operativo especificado por `osfhandle`. El argumento `flags` es una expresión de entero formada por una o varias de las constantes del manifiesto, definidas en Fcntl.h. Cuando se usan dos o más constantes del manifiesto para formar el argumento `flags`, estas constantes se combinan con el operador bit a bit OR (**&#124;**).  
  
 Fcntl.h define las siguientes constantes de manifiesto.  
  
 **_O_APPEND**  
 Coloca un puntero de archivo al final del archivo antes de cada operación de escritura.  
  
 **_O_RDONLY**  
 Abre el archivo únicamente para leerlo.  
  
 **_O_TEXT**  
 Abre el archivo en modo de texto (traducido).  
  
 **_O_WTEXT**  
 Abre el archivo en modo Unicode (UTF-16 traducido).  
  
 Para cerrar un archivo abierto con `_open_osfhandle`, llame a `_close`. El identificador subyacente también se cierra mediante una llamada a `_close`, por lo que no es necesario llamar a la función `CloseHandle` de Win32 en el identificador original.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_open_osfhandle`|\<io.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)
