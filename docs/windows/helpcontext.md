---
title: "helpcontext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.helpcontext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "helpcontext attribute"
ms.assetid: 6fbb022d-a4b7-4989-a02f-7f18a9b0ad96
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# helpcontext
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica un Id. de contexto que deje la información de la vista de usuario sobre este elemento en el archivo de Ayuda.  
  
## Sintaxis  
  
```  
  
      [ helpcontext(  
   id  
) ]  
```  
  
#### Parámetros  
 `id`  
 El Id. de contexto del tema de Ayuda.  Vea [Ayuda HTML: Ayuda contextual para los programas](../mfc/html-help-context-sensitive-help-for-your-programs.md) para obtener más información sobre id. de contexto.  
  
## Comentarios  
 el atributo de **helpcontext** C\+\+ tiene la misma funcionalidad que el atributo de [helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851) MIDL.  
  
## Ejemplo  
 Vea el ejemplo para [defaultvalue](../Topic/defaultvalue.md) para obtener un ejemplo de cómo utilizar **helpcontext**.  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|`interface`, `typedef`, **clase**, método, propiedad|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [helpfile](../Topic/helpfile.md)   
 [helpstring](../windows/helpstring.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)