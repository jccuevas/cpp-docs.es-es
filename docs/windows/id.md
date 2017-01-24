---
title: "id | Microsoft Docs"
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
  - "vc-attr.id"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "id attribute"
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# id
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica un parámetro de `dispid` para una función miembro \(una propiedad o método, en una interfaz o dispinterface\).  
  
## Sintaxis  
  
```  
  
      [ id(  
   dispid  
) ]  
```  
  
#### Parámetros  
 `dispid`  
 El identificador de envío para el método de interfaz.  
  
## Comentarios  
 el atributo de **ID** C\+\+ tiene la misma funcionalidad que el atributo de [ID](http://msdn.microsoft.com/library/windows/desktop/aa367040) MIDL.  
  
## Ejemplo  
 Vea el ejemplo para [enlazable](../windows/bindable.md) para obtener un ejemplo de cómo utilizar **ID**.  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|método de interfaz|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [Data Member Attributes](../windows/data-member-attributes.md)   
 [defaultvalue](../Topic/defaultvalue.md)   
 [in](../Topic/in%20\(C++\).md)   
 [Fuera](../Topic/out%20\(C++\).md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)