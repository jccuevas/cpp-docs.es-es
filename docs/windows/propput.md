---
title: "propput | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.propput"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "propput attribute"
ms.assetid: 1f84dda9-9cce-4e16-aaf0-b2c5219827f2
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# propput
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica una función de valor de propiedad.  
  
## Sintaxis  
  
```  
  
[propput]  
  
```  
  
## Comentarios  
 El atributo C\+\+ **propput** tiene la misma funcionalidad que el atributo MIDL [propput](http://msdn.microsoft.com/library/windows/desktop/aa367146).  
  
## Ejemplo  
 Consulte el ejemplo de [bindable](../windows/bindable.md) para ver un ejemplo de uso de **propput**.  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Método|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|**propget** y **propputref**|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [propget](../windows/propget.md)   
 [propputref](../windows/propputref.md)