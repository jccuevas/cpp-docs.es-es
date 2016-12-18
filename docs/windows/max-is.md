---
title: "max_is | Microsoft Docs"
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
  - "vc-attr.max_is"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "max_is attribute"
ms.assetid: 7c851f5c-6649-4d77-a792-247c37d8f560
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# max_is
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Indica el valor máximo de un índice válido de la matriz.  
  
## Sintaxis  
  
```  
  
      [ max_is(  
   "expression"  
) ]  
```  
  
#### Parámetros  
 *expresión*  
 Una o más expresiones del lenguaje C.  Se permiten las ranuras vacías del argumento.  
  
## Comentarios  
 el atributo de **max\_is** C\+\+ tiene la misma funcionalidad que el atributo de [max\_is](http://msdn.microsoft.com/library/windows/desktop/aa367074) MIDL.  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Campo de `struct` o **union**, parámetro de interfaz, método de interfaz|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|**size\_is**|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Ejemplo  
 Vea [first\_is](../windows/first-is.md) para obtener un ejemplo de cómo especificar una sección de una matriz.  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Parameter Attributes](../windows/parameter-attributes.md)   
 [first\_is](../windows/first-is.md)   
 [last\_is](../windows/last-is.md)   
 [length\_is](../windows/length-is.md)   
 [size\_is](../Topic/size_is.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)