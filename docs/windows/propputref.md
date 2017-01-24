---
title: "propputref | Microsoft Docs"
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
  - "vc-attr.propputref"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "propputref attribute"
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# propputref
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica una función de la configuración de propiedades que utilice una referencia en lugar de un valor.  
  
## Sintaxis  
  
```  
  
[propputref]  
  
```  
  
## Comentarios  
 el atributo de **propputref** C\+\+ tiene la misma funcionalidad que el atributo de [propputref](http://msdn.microsoft.com/library/windows/desktop/aa367147) MIDL.  
  
## Ejemplo  
 Vea el ejemplo para [enlazable](../windows/bindable.md) para un ejemplo de uso de **propputref**.  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Método|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|**propget**, **propput**|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [propget](../windows/propget.md)   
 [propput](../windows/propput.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)