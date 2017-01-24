---
title: "InspectableClass (Macro) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::InspectableClass"
dev_langs: 
  - "C++"
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# InspectableClass (Macro)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Establece el nombre de clase en tiempo de ejecución y el nivel de confianza.  
  
## Sintaxis  
  
```cpp  
  
InspectableClass(  
   runtimeClassName,   
   trustLevel)  
  
```  
  
#### Parámetros  
 `runtimeClassName`  
 Nombre textual completo de la clase en tiempo de ejecución.  
  
 `trustLevel`  
 Uno de los valores enumerados de [TrustLevel](http://msdn.microsoft.com/library/br224625.aspx).  
  
## Comentarios  
 La macro de `InspectableClass` solo se puede usar con los tipos [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)].  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [RuntimeClass \(Clase\)](../windows/runtimeclass-class.md)