---
title: "entry | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.entry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "entry attribute"
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# entry
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica una función o una constante exportada en un módulo identifica el punto de entrada en el archivo DLL.  
  
## Sintaxis  
  
```  
  
      [ entry(  
   id  
) ]  
```  
  
#### Parámetros  
 `id`  
 El identificador de punto de entrada.  
  
## Comentarios  
 el atributo de **entrada** C\+\+ tiene la misma funcionalidad que el atributo de [entrada](http://msdn.microsoft.com/library/windows/desktop/aa366815) MIDL.  
  
## Ejemplo  
 Vea el ejemplo para [idl\_module](../windows/idl-module.md) para un ejemplo de uso de **entrada**.  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Atributo `idl_module`|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)