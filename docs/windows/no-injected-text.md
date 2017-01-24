---
title: "no_injected_text | Microsoft Docs"
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
  - "vc-attr.no_injected_text"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "no_injected_text attribute"
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# no_injected_text
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Evita que el compilador inserte código como resultado de uso del atributo.  
  
## Sintaxis  
  
```  
  
      [ no_injected_text(  
   boolean  
) ];  
```  
  
#### Parámetros  
 `boolean`\(opcional\)  
 **TRUE** si no desea ningún código insertado, **Falso** para permitir que el código sea insertado.  **TRUE** es el valor predeterminado.  
  
## Comentarios  
 El uso más común del atributo de **no\_injected\_text** C\+\+ es para la opción del compilador [\/Fx](../build/reference/fx-merge-injected-code.md) , que inserta el atributo de **no\_injected\_text** en el archivo de .mrg.  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Cualquier parte|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [Compiler Attributes](../windows/compiler-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)