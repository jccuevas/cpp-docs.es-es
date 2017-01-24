---
title: "fwide | Microsoft Docs"
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
  - "fwide"
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
  - "fwide"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fwide (función)"
ms.assetid: a4641f5b-d74f-4946-95d5-53a64610d28d
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fwide
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Sin implementar.  
  
## Sintaxis  
  
```  
int fwide(  
   FILE *stream,  
   int mode;  
);  
```  
  
#### Parámetros  
 `stream`  
 Puntero a la estructura de `FILE` \(omitido\).  
  
 `mode`  
 El nuevo ancho de secuencia: positivo por carácter ancho, negativo para byte, cero dejar sin modificar. \(Se omite este valor.\)  
  
## Valor devuelto  
 Esta función solo devuelve actualmente `mode`.  
  
## Comentarios  
 La versión actual de esta función no cumple la norma.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`fwide`|\<wchar.h\>|  
  
 Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).