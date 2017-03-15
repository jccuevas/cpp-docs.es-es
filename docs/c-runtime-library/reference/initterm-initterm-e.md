---
title: "_initterm, _initterm_e | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_initterm_e"
  - "_initterm"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_initterm_e"
  - "initterm"
  - "_initterm"
  - "initterm_e"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "initterm (función)"
  - "initterm_e (función)"
  - "_initterm (función)"
  - "_initterm_e (función)"
ms.assetid: 85131efe-c747-429a-8897-bcdedb000172
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# _initterm, _initterm_e
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Métodos internos que explican una tabla de punteros a función y se inicializan ellos.  
  
 El primer puntero es la ubicación inicial de la tabla y el segundo puntero es la ubicación de cierre.  
  
## Sintaxis  
  
```  
void __cdecl _initterm(  
   PVFV *,  
   PVFV *  
);  
  
int __cdecl _initterm_e(  
   PVFV *,  
   PVFV *  
);  
```  
  
## Valor devuelto  
 Un código de error distinto de cero si una inicialización produce un error y produce un error; 0 si no se produce ningún error.  
  
## Comentarios  
 Estos métodos se llaman únicamente internamente durante la inicialización del programa de c\+\+.  No llame a estos métodos en un programa.  
  
 Cuando el recorrido de estos métodos una tabla de entradas de la función, ellos omitir las entradas de `NULL` y continúa.  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)