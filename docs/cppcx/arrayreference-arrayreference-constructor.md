---
title: "ArrayReference::ArrayReference (Constructor) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::ArrayReference::ArrayReference"
dev_langs: 
  - "C++"
ms.assetid: 9fc7dfcf-47af-40ba-a697-da476fb90efc
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# ArrayReference::ArrayReference (Constructor)
Inicializa una nueva instancia de la clase [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md).  
  
## Sintaxis  
  
```cpp  
ArrayReference(TArg* ataArg, unsigned int sizeArg, bool needsInitArg = false);  
ArrayReference(ArrayReference&& otherArg)  
  
```  
  
#### Parámetros  
 `dataArg`  
 Puntero a los datos de matriz.  
  
 `sizeArg`  
 Número de elementos de la matriz de origen.  
  
 `otherArg`  
 Objeto `ArrayReference` cuyos datos se moverán para inicializar la nueva instancia.  
  
## Comentarios  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Encabezado:** vccorlib.h  
  
## Vea también  
 [Platform::ArrayReference \(Clase\)](../cppcx/platform-arrayreference-class.md)   
 [Array y WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)