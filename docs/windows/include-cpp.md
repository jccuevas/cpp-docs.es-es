---
title: "include (C++) | Microsoft Docs"
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
  - "vc-attr.include"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "include attribute"
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# include (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica uno o más archivos de encabezado que se incluirán en el archivo generado .idl.  
  
## Sintaxis  
  
```  
  
      [ include(  
   header_file  
) ];  
```  
  
#### Parámetros  
 *header\_file*  
 El nombre de un archivo que desee incluir en el archivo generado .idl.  
  
## Comentarios  
 El atributo de **incluir** C\+\+ genera una instrucción de `#include` se coloque debajo de la instrucción de `import "docobj.idl"` en el archivo generado .idl.  
  
 el atributo de **incluir** C\+\+ tiene la misma funcionalidad que el atributo de [incluir](http://msdn.microsoft.com/library/windows/desktop/aa367052) MIDL.  
  
## Ejemplo  
 El código siguiente se muestra un ejemplo de cómo utilizar **incluir**.  Para este ejemplo, el archivo include.h sólo contiene una instrucción \#include.  
  
```  
// cpp_attr_ref_include.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[include(cpp_attr_ref_include.h)];  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Cualquier parte|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Stand\-Alone Attributes](../Topic/Stand-Alone%20Attributes.md)   
 [import](../windows/import.md)   
 [importidl](../windows/importidl.md)   
 [includelib](../windows/includelib-cpp.md)   
 [importlib](../windows/importlib.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)