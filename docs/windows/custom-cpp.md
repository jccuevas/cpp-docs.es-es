---
title: "custom (C++) | Microsoft Docs"
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
  - "vc-attr.custom"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "custom attributes, defining"
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# custom (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define los metadatos para un objeto de la biblioteca de tipos.  
  
## Sintaxis  
  
```  
  
      [ custom(  
   uuid,   
   value  
) ];  
```  
  
#### Parámetros  
 *uuid*  
 Identificador único.  
  
 *valor*  
 Un valor que se puede incluir en una variante.  
  
## Comentarios  
 El atributo de **personalizada** C\+\+ hará que la información se coloque en la biblioteca de tipos.  Necesitará una herramienta que lee el valor personalizado de la biblioteca de tipos.  
  
 el atributo de **personalizada** tiene la misma funcionalidad que el atributo de [personalizada](http://msdn.microsoft.com/library/windows/desktop/aa366766) MIDL.  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|No\-COM `interface`, **clase**, s de `enum`, métodos de `idl_module` , miembros de interfaz, parámetros de interfaz, s de `typedef`, s de **union**, s de `struct`|  
|**repetible**|Sí|  
|**Atributos necesarios**|**CoClass** \(cuando se utiliza en clase\)|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Stand\-Alone Attributes](../Topic/Stand-Alone%20Attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Parameter Attributes](../windows/parameter-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)