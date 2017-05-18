---
title: _CrtSetDumpClient | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtSetDumpClient
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
apitype: DLLExport
f1_keywords:
- _CrtSetDumpClient
- CrtSetDumpClient
dev_langs:
- C++
helpviewer_keywords:
- _CrtSetDumpClient function
- CrtSetDumpClient function
ms.assetid: f3dd06d0-c331-4a12-b68d-25378d112033
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 0fc4875a344a8d094c40436ae6d67d80707deef1
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="crtsetdumpclient"></a>_CrtSetDumpClient
Instala una función definida por la aplicación para volcar bloques de memoria de tipo `_CLIENT_BLOCK` (solo versión de depuración).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      _CRT_DUMP_CLIENT _CrtSetDumpClient(   
   _CRT_DUMP_CLIENT dumpClient   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dumpClient`  
 Nueva función de volcado de memoria definida por el cliente que se va a enlazar al proceso de volcado de memoria de depuración en tiempo de ejecución de C.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve la función previamente definida de volcado de bloques de cliente.  
  
## <a name="remarks"></a>Comentarios  
 La función `_CrtSetDumpClient` permite que la aplicación enlace su propia función para volcar objetos almacenados en bloques de memoria `_CLIENT_BLOCK` en el proceso de volcado de memoria de depuración en tiempo de ejecución de C. Por consiguiente, cada vez que una función de volcado de depuración como [_CrtMemDumpAllObjectsSince](../../c-runtime-library/reference/crtmemdumpallobjectssince.md) o [_CrtDumpMemoryLeaks](../../c-runtime-library/reference/crtdumpmemoryleaks.md) vuelcan un bloque de memoria `_CLIENT_BLOCK`, también se llama a la función de volcado de la aplicación. `_CrtSetDumpClient` proporciona a una aplicación un método sencillo para detectar pérdidas de memoria, y validar o notificar el contenido de los datos almacenados en bloques `_CLIENT_BLOCK`. Cuando no se define [_DEBUG](../../c-runtime-library/debug.md), las llamadas a `_CrtSetDumpClient` se quitan durante el preprocesamiento.  
  
 La función `_CrtSetDumpClient` instala la nueva función de volcado definida por la aplicación especificada en `dumpClient` y devuelve la función de volcado definida previamente. Ejemplo de una función de volcado de bloque de cliente:  
  
```  
void DumpClientFunction( void *userPortion, size_t blockSize );  
```  
  
 El argumento `userPortion` es un puntero al principio de la parte de datos del usuario del bloque de memoria y `blockSize` especifica en bytes el tamaño del bloque de memoria asignado. La función de volcado de bloque de cliente debe devolver `void`. El puntero a la función de volcado de cliente que se pasa a `_CrtSetDumpClient` es del tipo `_CRT_DUMP_CLIENT`, según se define en Crtdbg.h:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)( void *, size_t );  
```  
  
 Para obtener más información sobre funciones que se usan con bloques de memoria de tipo `_CLIENT_BLOCK`, consulte [Funciones de enlace con los bloques de tipo cliente](/visualstudio/debugger/client-block-hook-functions). La función [_CrtReportBlockType](../../c-runtime-library/reference/crtreportblocktype.md) se puede usar para devolver información sobre los tipos y subtipos de bloques.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_CrtSetDumpClient`|\<crtdbg.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [_CrtReportBlockType](../../c-runtime-library/reference/crtreportblocktype.md)   
 [_CrtGetDumpClient](../../c-runtime-library/reference/crtgetdumpclient.md)
