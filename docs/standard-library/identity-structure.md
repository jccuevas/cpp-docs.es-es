---
title: "identity (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::identity"
  - "utility/std::identity"
  - "identity"
  - "std.identity"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "identity (clase)"
  - "identity (estructura)"
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
caps.latest.revision: 15
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# identity (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Struct que proporciona una definición de tipo como parámetro de plantilla.  
  
## Sintaxis  
  
```  
template<class Type>  
   struct identity {  
      typedef Type type;  
      Type operator()(const Type& _Left) const;  
   };  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`_Left`|El valor a identificar.|  
  
## Comentarios  
 La clase contiene la definición de tipo pública `type`, que es el mismo que el tipo de parámetro de plantilla.  Se utiliza junto con la función [forward](../Topic/forward.md) de plantilla para garantizar que un parámetro de la función tiene el tipo deseado.  
  
 Para la compatibilidad con el anterior código, la clase también define la función de identidad `operator()` que devuelve el argumento `_Left`.  
  
## Requisitos  
 utilidad \<de**Encabezado:** \>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<utility\>](../standard-library/utility.md)