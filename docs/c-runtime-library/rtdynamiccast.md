---
title: "__RTDynamicCast | Microsoft Docs"
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
  - "__RTDynamicCast"
apilocation: 
  - "msvcr90.dll"
  - "msvcr110.dll"
  - "msvcr120.dll"
  - "msvcrt.dll"
  - "msvcr100.dll"
  - "msvcr80.dll"
  - "msvcr110_clr0400.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__RTDynamicCast"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__RTDynamicCast"
ms.assetid: 56aa2d7a-aa47-46ef-830d-e37175611239
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __RTDynamicCast
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Implementación en tiempo de ejecución del operador de [dynamic\_cast](../cpp/dynamic-cast-operator.md) .  
  
## Sintaxis  
  
```cpp  
PVOID __RTDynamicCast (  
   PVOID inptr,   
   LONG VfDelta,  
   PVOID SrcType,  
   PVOID TargetType,   
   BOOL isReference  
   ) throw(...)  
```  
  
#### Parámetros  
 `inptr`  
 Puntero a un objeto polimórfico.  
  
 `VfDelta`  
 Desplazamiento del puntero a función virtual de objeto.  
  
 `SrcType`  
 De tipo estático del objeto proporcionado por el parámetro de `inptr` .  
  
 `TargetType`  
 Resultado previsto de la conversión.  
  
 `isReference`  
 `true` si la entrada es una referencia; `false` si la entrada es un puntero.  
  
## Valor devuelto  
 Puntero al sub\- objeto adecuado, si correctamente; de lo contrario, NULL.  
  
## Excepciones  
 `bad_cast()` si la entrada a `dynamic_cast<>` es una referencia y la conversión no se produce.  
  
## Comentarios  
 Convierte `inptr` a un objeto de `TargetType`escrito.  El tipo de `inptr` debe ser un puntero si `TargetType` es un puntero, o un valor L si `TargetType` es una referencia.  `TargetType` debe ser un puntero o una referencia a un tipo de clase previamente definido, o puntero a null.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|\_\_RTDynamicCast|rtti.h|