---
title: "retval | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.retval"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "retval attribute"
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# retval
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Designa el parámetro que recibe el valor devuelto del miembro.  
  
## Sintaxis  
  
```  
  
[retval]  
  
```  
  
## Comentarios  
 el atributo de **retval** C\+\+ tiene la misma funcionalidad que el atributo de [retval](http://msdn.microsoft.com/library/windows/desktop/aa367158) MIDL.  
  
 **retval** debe aparecer en el último argumento en una declaración de función.  
  
## Ejemplo  
 Vea el ejemplo para [enlazable](../windows/bindable.md) para un ejemplo de uso de **retval**.  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Parámetro de interfaz, método de interfaz|  
|**repetible**|No|  
|**Atributos necesarios**|**out**|  
|**Atributos no válidos**|**in**|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Parameter Attributes](../windows/parameter-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)