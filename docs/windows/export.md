---
title: "export | Microsoft Docs"
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
  - "vc-attr.export"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "export attribute"
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# export
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Genera una estructura de datos que se almacena en el archivo .idl.  
  
## Sintaxis  
  
```  
  
[export]  
  
```  
  
## Comentarios  
 El atributo de **Exportar** C\+\+ genera una estructura de datos que se almacena en el archivo .idl y después a estar disponible en la biblioteca de tipos en un formato de binario\-compatible que está disponible para su uso con cualquier lenguaje.  
  
 No puede aplicar el atributo de **Exportar** a una clase incluso si la clase tiene sólo los miembros públicos \(el equivalente de `struct`\).  
  
 Si exporta s sin nombre de `enum`o s para `struct`, se con nombres que comienzan por **\_\_unnamed***x*, donde es un número *x* secuencial.  
  
 Tipos válidos para la exportación son tipos base, structs, uniones, enumeraciones, o identificadores de tipo.  Vea [typedef](http://msdn.microsoft.com/library/windows/desktop/aa367287) para obtener más información.  
  
## Ejemplo  
 el código siguiente muestra cómo utilizar el atributo de **Exportar** :  
  
```  
// cpp_attr_ref_export.cpp  
// compile with: /LD  
[module(name="MyLibrary")];  
  
[export]  
struct MyStruct {  
   int i;  
};  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**union**, `typedef`, `enum`, `struct`, o `interface`|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [Compiler Attributes](../windows/compiler-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)