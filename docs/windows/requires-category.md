---
title: "requires_category | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.requires_category"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "requires_category attribute"
ms.assetid: a645fdc6-1ef5-414d-8c56-5fe2686d4687
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# requires_category
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica las categorías componentes necesarias de la clase de destino.  
  
## Sintaxis  
  
```  
  
     [ requires_category(   
  requires_category  
) ]  
```  
  
#### Parámetros  
 *requires\_category*  
 El identificador de categoría necesaria.  
  
## Comentarios  
 El atributo de **requires\_category** C\+\+ especifica las categorías componentes requeridas por la clase de destino.  Para obtener más información, vea [REQUIRED\_CATEGORY](../Topic/REQUIRED_CATEGORY.md).  
  
 Este atributo requiere que [CoClass](../windows/coclass.md), [ProgID](../Topic/progid.md), o el atributo de [vi\_progid](../windows/vi-progid.md) \(u otro atributo que implica una de estas\) también se aplican al mismo elemento.  
  
## Ejemplo  
 El código siguiente requiere que implementan el objeto la categoría del Control.  
  
```  
// cpp_attr_ref_requires_category.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name="MyLibrary")];  
  
[ coclass, requires_category("CATID_Control"),  
  uuid("1e1a2436-f3ea-4ff3-80bf-5409370e8144")]  
class CMyClass {};  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase**, `struct`|  
|**repetible**|No|  
|**Atributos necesarios**|Uno o más de los siguientes: **CoClass**, **ProgID**, o **vi\_progid**.|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [COM Attributes](../Topic/COM%20Attributes.md)   
 [implements\_category](../Topic/implements_category.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)