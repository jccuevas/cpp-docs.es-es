---
title: "includelib (C++) | Microsoft Docs"
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
  - "vc-attr.includelib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "includelib attribute"
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# includelib (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Produce un archivo .idl o .h que se incluirá en el archivo generado .idl.  
  
## Sintaxis  
  
```  
  
      [ includelib(  
   name.idl  
) ];  
```  
  
#### Parámetros  
 *name.idl*  
 El nombre del archivo .idl que desee incluir como parte del archivo generado .idl.  
  
## Comentarios  
 El atributo de `includelib` C\+\+ produce un archivo .idl o .h que se incluirá en el archivo generado .idl, después de la instrucción de `importlib` .  
  
## Ejemplo  
 El código siguiente se muestra en un archivo .cpp:  
  
```  
// cpp_attr_ref_includelib.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[includelib("includelib.idl")];  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Cualquier parte|  
|**repetible**|Sí|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Stand\-Alone Attributes](../Topic/Stand-Alone%20Attributes.md)   
 [import](../windows/import.md)   
 [importidl](../windows/importidl.md)   
 [include](../windows/include-cpp.md)   
 [importlib](../windows/importlib.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)