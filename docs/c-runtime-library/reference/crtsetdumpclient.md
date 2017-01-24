---
title: "_CrtSetDumpClient | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtSetDumpClient"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_CrtSetDumpClient"
  - "CrtSetDumpClient"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_CrtSetDumpClient (función)"
  - "CrtSetDumpClient (función)"
ms.assetid: f3dd06d0-c331-4a12-b68d-25378d112033
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtSetDumpClient
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Instala una función definida por la aplicación para volcar bloques de memoria de tipo `_CLIENT_BLOCK` \(solo versión de depuración\).  
  
## Sintaxis  
  
```  
  
      _CRT_DUMP_CLIENT _CrtSetDumpClient(   
   _CRT_DUMP_CLIENT dumpClient   
);  
```  
  
#### Parámetros  
 `dumpClient`  
 Nueva función de volcado de memoria definida por el cliente que se va a enlazar al proceso de volcado de memoria de depuración en tiempo de ejecución de C.  
  
## Valor devuelto  
 Devuelve la función previamente definida de volcado de bloques de cliente.  
  
## Comentarios  
 La función `_CrtSetDumpClient` permite que la aplicación enlace su propia función para volcar objetos almacenados en bloques de memoria `_CLIENT_BLOCK` en el proceso de volcado de memoria de depuración en tiempo de ejecución de C.  Como resultado, cada vez que una función de volcado de depuración como [\_CrtMemDumpAllObjectsSince](../../c-runtime-library/reference/crtmemdumpallobjectssince.md) o [\_CrtDumpMemoryLeaks](../../c-runtime-library/reference/crtdumpmemoryleaks.md) vuelca un bloque de memoria `_CLIENT_BLOCK`, también se llama a la función de volcado de la aplicación.  `_CrtSetDumpClient` proporciona a una aplicación un método sencillo para detectar pérdidas de memoria, y validar o notificar el contenido de los datos almacenados en bloques `_CLIENT_BLOCK`.  Cuando no se define [\_DEBUG](../../c-runtime-library/debug.md), las llamadas a `_CrtSetDumpClient` se quitan durante el preprocesamiento.  
  
 La función `_CrtSetDumpClient` instala la nueva función de volcado definida por la aplicación especificada en `dumpClient` y devuelve la función de volcado definida previamente.  Ejemplo de una función de volcado de bloque de cliente:  
  
```  
void DumpClientFunction( void *userPortion, size_t blockSize );  
```  
  
 El argumento `userPortion` es un puntero al principio de la parte de datos del usuario del bloque de memoria y `blockSize` especifica en bytes el tamaño del bloque de memoria asignado.  La función de volcado de bloque de cliente debe devolver `void`.  El puntero a la función de volcado de cliente que se pasa a `_CrtSetDumpClient` es del tipo `_CRT_DUMP_CLIENT`, según se define en Crtdbg.h:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)( void *, size_t );  
```  
  
 Para obtener más información sobre funciones que se usan con bloques de memoria de tipo `_CLIENT_BLOCK`, vea [Funciones de enlace con los bloques de tipo cliente](../Topic/Client%20Block%20Hook%20Functions.md).  La función [\_CrtReportBlockType](../../c-runtime-library/reference/crtreportblocktype.md) se puede usar para devolver información sobre los tipos y subtipos de los bloques.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_CrtSetDumpClient`|\<crtdbg.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Solo las versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [\_CrtReportBlockType](../../c-runtime-library/reference/crtreportblocktype.md)   
 [\_CrtGetDumpClient](../../c-runtime-library/reference/crtgetdumpclient.md)