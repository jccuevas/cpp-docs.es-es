---
title: "String::CompareOrdinal (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::CompareOrdinal"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::CompareOrdinal"
ms.assetid: dd4a7acc-fd23-4f1e-af85-64b9086f63f8
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::CompareOrdinal (M&#233;todo)
Compara dos objetos `String` mediante la evaluación de los valores numéricos de los caracteres correspondientes en los dos valores alfanuméricos representados por los objetos.  
  
## Sintaxis  
  
```cpp  
  
int CompareOrdinal(  
           String^ str1,   
           String^ str2)  
  
```  
  
#### Parámetros  
 `str1`  
 El primer objeto String.  
  
 `str2`  
 El segundo objeto String.  
  
## Valor devuelto  
 Entero que indica la relación léxica que existe entre los dos términos de una comparación. La tabla siguiente muestra los valores devueltos posibles.  
  
|Valor|Condición|  
|-----------|---------------|  
|\-1|`str1` es menor que `str2`.|  
|0|`str1` es igual que `str2`.|  
|1|`str1` es mayor que `str2`.|  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** vccorlib.h  
  
## Vea también  
 [Platform::String \(Clase\)](../cppcx/platform-string-class.md)