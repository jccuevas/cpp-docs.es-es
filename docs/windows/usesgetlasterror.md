---
title: "usesgetlasterror | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.usesgetlasterror"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "usesgetlasterror attribute"
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# usesgetlasterror
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Indica al llamador que si hay un error al llamar a la función, el llamador puede llamar `GetLastError` para recuperar el código de error.  
  
## Sintaxis  
  
```  
  
[usesgetlasterror]  
  
```  
  
## Comentarios  
 el atributo de **usesgetlasterror** C\+\+ tiene la misma funcionalidad que el atributo de [usesgetlasterror](http://msdn.microsoft.com/library/windows/desktop/aa367297) MIDL.  
  
## Ejemplo  
 Vea el ejemplo de [idl\_module](../windows/idl-module.md) para obtener un ejemplo de cómo utilizar **usesgetlasterror**.  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|atributo de**módulo**|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)