---
title: "importidl | Microsoft Docs"
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
  - "vc-attr.importidl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "importidl attribute"
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# importidl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Inserta el archivo especificado .idl en el archivo generado .idl.  
  
## Sintaxis  
  
```  
  
      [ importidl(  
   idl_file  
) ];  
```  
  
#### Parámetros  
 `idl_file`  
 Identifica el nombre del archivo .idl que desea combinar con el archivo .idl que se generará para la aplicación.  
  
## Comentarios  
 El atributo de **importidl** C\+\+ coloca la sección fuera del bloque de biblioteca \(en `idl_file`\) en el archivo generado .idl del programa y la sección biblioteca \(en `idl_file`\) en la sección de la biblioteca del archivo generado .idl del programa.  
  
 Se puede utilizar **importidl**, por ejemplo, si desea utilizar un archivo mano\-codificado .idl con el archivo generado .idl.  
  
## Ejemplo  
  
```  
// cpp_attr_ref_importidl.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[importidl("import.idl")];  
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
 [Compiler Attributes](../windows/compiler-attributes.md)   
 [Stand\-Alone Attributes](../Topic/Stand-Alone%20Attributes.md)   
 [import](../windows/import.md)   
 [importlib](../windows/importlib.md)   
 [include](../windows/include-cpp.md)   
 [includelib](../windows/includelib-cpp.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)