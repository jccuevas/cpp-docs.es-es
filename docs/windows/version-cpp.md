---
title: "version (C++) | Microsoft Docs"
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
  - "vc-attr.version"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "version attribute"
  - "version information, version attribute"
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# version (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Identifica una determinada versión entre varias versiones de una clase.  
  
## Sintaxis  
  
```  
  
      [ version(  
   "version"  
) ]  
```  
  
#### Parámetros  
 *versión*  
 El número de versión de la coclase.  Si no se especifica, 1,0 se incluirán en el archivo .idl.  
  
## Comentarios  
 El atributo de **versión** C\+\+ tiene la misma funcionalidad que el atributo de [versión](http://msdn.microsoft.com/library/windows/desktop/aa367306) MIDL y se pasan al archivo generado .idl.  
  
## Ejemplo  
 Vea el ejemplo de [enlazable](../windows/bindable.md) para un ejemplo de uso de **versión**.  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase**, `struct`|  
|**repetible**|No|  
|**Atributos necesarios**|**CoClass**|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [Compiler Attributes](../windows/compiler-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)