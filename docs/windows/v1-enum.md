---
title: "v1_enum | Microsoft Docs"
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
  - "vc-attr.v1_enum"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "v1_enum attribute"
ms.assetid: 2fe92d92-81b9-4a1c-b6ce-437d0eb770ca
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# v1_enum
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Dirige que transmiten al tipo enumerado especificado como entidad de 32 bits en lugar del valor predeterminado de 16 bits.  
  
## Sintaxis  
  
```  
  
[v1_enum]  
  
```  
  
## Comentarios  
 el atributo de **v1\_enum** C\+\+ tiene la misma funcionalidad que el atributo de [v1\_enum](http://msdn.microsoft.com/library/windows/desktop/aa367303) MIDL.  
  
## Ejemplo  
 El código siguiente se muestra un uso de **v1\_enum**:  
  
```  
// cpp_attr_ref_v1_enum.cpp  
// compile with: /LD  
[module(name="MyLibrary")];  
  
[export, v1_enum]   
enum eList {   
   e1 = 1,   
   e2 = 2  
};  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|tipo enumerado|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)