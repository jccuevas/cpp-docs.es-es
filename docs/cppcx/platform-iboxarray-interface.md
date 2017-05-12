---
title: "Platform::IBoxArray (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::IBoxArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::IBoxArray"
ms.assetid: 6cd82c9e-4230-4147-9edb-7a652875dbf1
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 5
---
# Platform::IBoxArray (Interfaz)
`IBoxArray` es el contenedor de matrices de los tipos de valor que se pasan a través de la interfaz binaria de aplicación \(ABI\) o se almacenan en colecciones de elementos `Platform::Object^` como los de los controles XAML.  
  
## Sintaxis  
  
```cpp  
template <typename T>  
interface class IBoxArray  
```  
  
#### Parámetros  
 `T`  
 Tipo del valor al que se ha aplicado la conversión boxing en cada elemento de la matriz.  
  
## Comentarios  
 `IBoxArray` es el nombre de [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] \([!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]\) para `Windows::Foundation::IReferenceArray`.  
  
## Miembros  
 La interfaz `IBoxArray` hereda de la interfaz `IValueType`.`IBoxArray` también tiene estos miembros:  
  
|Método|Descripción|  
|------------|-----------------|  
|Valor|Devuelve la matriz a la que se le ha aplicado la conversión unboxing y que se almacenó previamente en esta instancia de `IBoxArray`.|  
  
## Vea también  
 [Array y WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)