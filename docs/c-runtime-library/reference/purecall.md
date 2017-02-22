---
title: "_purecall | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_purecall"
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
  - "ntoskrnl.exe"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "purecall"
  - "_purecall"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_purecall (función)"
  - "purecall (función)"
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# _purecall
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El controlador de errores de llamada de función virtual pura de forma predeterminada. El compilador genera código para llamar a esta función cuando se llama a una función miembro virtual pura.  
  
## Sintaxis  
  
```  
extern "C" int __cdecl _purecall();  
```  
  
## Comentarios  
 El `_purecall` función es un detalle de implementación específicos de Microsoft del compilador de Microsoft Visual C\+\+. Esta función no está diseñada para ser llamado directamente por el código y no tiene encabezado público una declaración. Se documenta aquí porque es una exportación de la biblioteca en tiempo de ejecución de C pública.  
  
 Una llamada a una función virtual pura es un error porque no tiene ninguna implementación. El compilador genera código para invocar la `_purecall` función de controlador de errores cuando se llama a una función virtual pura. De forma predeterminada, `_purecall` finaliza el programa. Antes de terminar, la `_purecall` función invoca un `_purecall_handler` funcionar si se ha definido alguna para el proceso. Puede instalar su propia función de controlador de errores para las llamadas de función virtual pura, contagiarse para depurar o con fines informativos. Para utilizar su propio controlador de errores, cree una función que tiene el `_purecall_handler` firma, a continuación, utilice [\_set\_purecall\_handler](../../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md) para que sea el controlador actual.  
  
## Requisitos  
 El `_purecall` la función no tiene una declaración de encabezado. El `_purecall_handler` typedef se define en \< stdlib.h \>.  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [\_get\_purecall\_handler, \_set\_purecall\_handler](../../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md)