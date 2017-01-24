---
title: "_CxxThrowException | Microsoft Docs"
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
  - "_CxxThrowException"
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
  - "CxxThrowException"
  - "_CxxThrowException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CxxThrowException (función)"
  - "CxxThrowException (función)"
ms.assetid: 0b90bef5-b7d2-46e0-88e2-59e531e01a4d
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CxxThrowException
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Compila el registro de excepciones y llama al entorno en tiempo de ejecución para iniciar procesar la excepción.  
  
## Sintaxis  
  
```  
extern "C" void __stdcall _CxxThrowException(  
   void* pExceptionObject  
   _ThrowInfo* pThrowInfo  
);  
```  
  
#### Parámetros  
 \[in\] `pExceptionObject`  
 Objeto que produjo la excepción.  
  
 \[in\] `pThrowInfo`  
 La información necesaria para procesar la excepción.  
  
## Comentarios  
 Este método se incluye en un archivo del compilador \- sólo el compilador utilizará para procesar excepciones.  No llame al método directamente desde el código.  
  
## Requisitos  
 **Origen:** Throw.cpp  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)