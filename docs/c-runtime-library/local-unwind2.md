---
title: "_local_unwind2 | Microsoft Docs"
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
  - "_local_unwind2"
apilocation: 
  - "msvcr110_clr0400.dll"
  - "msvcrt.dll"
  - "msvcr100.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_local_unwind2"
  - "local_unwind2"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_local_unwind2 (función)"
  - "local_unwind2 (función)"
ms.assetid: 44f1fa82-e01e-490f-a6e6-18fc6811c28c
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _local_unwind2
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Función de CRT interna.  Ejecuta todos los controladores de finalización que figuran en la tabla de ámbito indicada.  
  
## Sintaxis  
  
```  
void _local_unwind2(    PEXCEPTION_REGISTRATION xr,    int stop );  
```  
  
#### Parámetros  
 \[in\] `xr`  
 Registro asociado a una tabla de ámbito.  
  
 \[in\] `stop`  
 Nivel léxico que señala dónde debe detenerse `_local_unwind2`.  
  
## Comentarios  
 Este método solo se usa en el entorno en tiempo de ejecución.  No llame a este método en su código.  
  
 Cuando este método ejecuta controladores de finalización, comienza en el nivel léxico actual y realiza su recorrido hacia niveles léxicos superiores hasta que alcanza el nivel indicado por `stop`.  No ejecuta controladores de finalización situados en el nivel indicado por `stop`.  
  
## Vea también  
 [Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)