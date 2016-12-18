---
title: "_CrtReportBlockType | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtReportBlockType"
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
  - "_CrtReportBlockType"
  - "CrtReportBlockType"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "CrtReportBlockType (función)"
  - "BLOCK_SUBTYPE (macro)"
  - "_CrtReportBlockType (función)"
  - "_BLOCK_TYPE (macro)"
  - "_BLOCK_SUBTYPE (macro)"
  - "BLOCK_TYPE (macro)"
ms.assetid: 0f4b9da7-bebb-4956-9541-b2581640ec6b
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtReportBlockType
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve el tipo o subtipo de bloque asociado a un puntero de bloque especificado del montón de depuración.  
  
## Sintaxis  
  
```  
  
      int _CrtReportBlockType(  
   const void * pBlock  
};  
```  
  
#### Parámetros  
 *pBlock*  
 Puntero a un bloque válido del montón de depuración.  
  
## Valor devuelto  
 Cuando se le pasa un puntero del montón de depuración válido, la función `_CrtReportBlockType` devuelve el tipo y subtipo de bloque en forma de `int`.  Cuando se le pasa un puntero no válido, la función devuelve \-1.  
  
## Comentarios  
 Para extraer el tipo y subtipo devueltos por `_CrtReportBlockType`, use las macros **\_BLOCK\_TYPE** y **\_BLOCK\_SUBTYPE** \(ambas definidas en Crtdbg.h\) en el valor devuelto.  
  
 Para obtener información sobre la asignación de tipos de bloque y cómo se usan, vea [Tipos de bloques en el montón de depuración](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_CrtReportBlockType`|\<crtdbg.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Solo las versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_crtreportblocktype.cpp  
// compile with: /MDd  
  
#include <malloc.h>  
#include <stdio.h>  
#include <crtdbg.h>  
  
void __cdecl Dumper(void *ptr, void *)  
{  
    int block = _CrtReportBlockType(ptr);  
    _RPT3(_CRT_WARN, "Dumper found block at %p: type %d, subtype %d\n", ptr,  
          _BLOCK_TYPE(block), _BLOCK_SUBTYPE(block));  
}  
  
void __cdecl LeakDumper(void *ptr, size_t sz)  
{  
    int block = _CrtReportBlockType(ptr);  
    _RPT4(_CRT_WARN, "LeakDumper found block at %p:"  
                     " type %d, subtype %d, size %d\n", ptr,  
          _BLOCK_TYPE(block), _BLOCK_SUBTYPE(block), sz);  
}  
  
int main(void)  
{  
    _CrtSetDbgFlag(_CrtSetDbgFlag(_CRTDBG_REPORT_FLAG) |   
    _CRTDBG_LEAK_CHECK_DF);  
    _CrtSetReportMode( _CRT_WARN, _CRTDBG_MODE_FILE );  
    _CrtSetReportFile( _CRT_WARN, _CRTDBG_FILE_STDOUT );  
    _malloc_dbg(10, _NORMAL_BLOCK , __FILE__, __LINE__);  
    _malloc_dbg(10, _CLIENT_BLOCK | (1 << 16), __FILE__, __LINE__);  
    _malloc_dbg(20, _CLIENT_BLOCK | (2 << 16), __FILE__, __LINE__);  
    _malloc_dbg(30, _CLIENT_BLOCK | (3 << 16), __FILE__, __LINE__);  
    _CrtDoForAllClientObjects(Dumper, NULL);  
    _CrtSetDumpClient(LeakDumper);  
}  
```  
  
## Resultados del ejemplo  
  
```  
Dumper found block at 00314F78: type 4, subtype 3  
Dumper found block at 00314F38: type 4, subtype 2  
Dumper found block at 00314F00: type 4, subtype 1  
Detected memory leaks!  
Dumping objects ->  
crt_crtreportblocktype.cpp(30) : {55} client block at 0x00314F78, subtype 3, 30 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
crt_crtreportblocktype.cpp(29) : {54} client block at 0x00314F38, subtype 2, 20 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
crt_crtreportblocktype.cpp(28) : {53} client block at 0x00314F00, subtype 1, 10 bytes long.  
 Data: <          > CD CD CD CD CD CD CD CD CD CD  
crt_crtreportblocktype.cpp(27) : {52} normal block at 0x00314EC8, 10 bytes long.  
 Data: <          > CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
## Vea también  
 [\_CrtDoForAllClientObjects](../../c-runtime-library/reference/crtdoforallclientobjects.md)   
 [\_CrtSetDumpClient](../../c-runtime-library/reference/crtsetdumpclient.md)   
 [\_CrtMemDumpAllObjectsSince](../../c-runtime-library/reference/crtmemdumpallobjectssince.md)   
 [\_CrtDumpMemoryLeaks](../../c-runtime-library/reference/crtdumpmemoryleaks.md)