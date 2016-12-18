---
title: "last_is | Microsoft Docs"
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
  - "vc-attr.last_is"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "last_is attribute"
ms.assetid: 9e045ac0-fa38-4249-af55-67bde5d0a58c
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# last_is
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica el índice del elemento de la matriz pasado que se transmitirá.  
  
## Sintaxis  
  
```  
  
      [ last_is(  
   "expression"  
) ]  
```  
  
#### Parámetros  
 *expresión*  
 Una o más expresiones del lenguaje C.  Se permiten las ranuras vacías del argumento.  
  
## Comentarios  
 el atributo de **last\_is** C\+\+ tiene la misma funcionalidad que el atributo de [last\_is](http://msdn.microsoft.com/library/windows/desktop/aa367066) MIDL.  
  
## Ejemplo  
 Vea [first\_is](../windows/first-is.md) para obtener un ejemplo de cómo especificar una sección de una matriz.  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Campo de `struct` o **union**, parámetro de interfaz, método de interfaz|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Parameter Attributes](../windows/parameter-attributes.md)   
 [first\_is](../windows/first-is.md)   
 [max\_is](../windows/max-is.md)   
 [length\_is](../windows/length-is.md)   
 [size\_is](../Topic/size_is.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)