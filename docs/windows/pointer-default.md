---
title: "pointer_default | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.pointer_default"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pointer_default attribute"
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# pointer_default
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica el atributo predeterminado de puntero para todos los punteros, excepto los punteros de nivel superior que aparecen en listas de parámetros.  
  
## Sintaxis  
  
```  
  
      [ pointer_default(  
   value  
) ]  
```  
  
#### Parámetros  
 *valor*  
 un valor que describe el tipo de puntero: **PTR**, `ref`, o **único**.  
  
## Comentarios  
 el atributo de **pointer\_default** C\+\+ tiene la misma funcionalidad que el atributo de [pointer\_default](http://msdn.microsoft.com/library/windows/desktop/aa367141) MIDL.  
  
## Ejemplo  
 Vea el ejemplo para [defaultvalue](../Topic/defaultvalue.md) para un ejemplo de uso de **pointer\_default**.  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|`interface`|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)