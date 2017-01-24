---
title: "__max | Microsoft Docs"
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
  - "__max"
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
  - "max"
  - "__max"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "__max (macro)"
  - "max (macro)"
  - "maximum (macro)"
ms.assetid: 05c936f6-0e22-45d6-a58d-4bc102e9dae2
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __max
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve el mayor de dos valores.  
  
## Sintaxis  
  
```  
type __max(  
   type a,  
   type b   
);  
```  
  
#### Parámetros  
 `type`  
 Cualquier tipo de datos numérico.  
  
 `a, b`  
 Valores de tipo numérico que se va a comparar.  
  
## Valor devuelto  
 `__max` devuelve el mayor de sus argumentos.  
  
## Comentarios  
 La macro de `__max` compara dos valores y devuelve el valor de mayor.  Los argumentos pueden ser de cualquier tipo de datos numérico, con signo o sin signo.  Los argumentos y el valor devuelto deben ser del mismo tipo de datos.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`__max`|\<stdlib.h\>|  
  
## Ejemplo  
 Para obtener más información, vea el ejemplo para [\_\_min](../../c-runtime-library/reference/min.md).  
  
## Equivalente en .NET Framework  
 [System::Math::Max](https://msdn.microsoft.com/en-us/library/system.math.max.aspx)  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [\_\_min](../../c-runtime-library/reference/min.md)