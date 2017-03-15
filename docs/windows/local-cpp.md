---
title: "local (C++) | Microsoft Docs"
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
  - "vc-attr.local"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "local attribute"
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# local (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se usa en el encabezado de la interfaz, permite utilizar el compilador MIDL como generador de encabezado.  Cuando se utiliza en una función individual, elija un procedimiento local para el que no se genera ningún códigos auxiliares.  
  
## Sintaxis  
  
```  
  
[local]  
  
```  
  
## Comentarios  
 el atributo de `local` C\+\+ tiene la misma funcionalidad que el atributo de [local](http://msdn.microsoft.com/library/windows/desktop/aa367071) MIDL.  
  
## Ejemplo  
 Vea [call\_as](../windows/call-as.md) para obtener un ejemplo de cómo utilizar `local`.  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|`interface`, método de interfaz|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|**dispinterface**|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [call\_as](../windows/call-as.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)