---
title: "&lt;value&gt; (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "value"
  - "<value>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<value> (etiqueta XML) [C++]"
  - "value (etiqueta XML) [C++]"
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;value&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La etiqueta de \<value\> permite describir métodos de una propiedad y el descriptor de acceso de la propiedad.  Tenga en cuenta que cuando se agrega una propiedad con el asistente para código en el entorno de desarrollo integrado de Visual Studio, agregará una etiqueta de [\<summary\>](../ide/summary-visual-cpp.md) para la nueva propiedad.  A continuación, se debe agregar manualmente una etiqueta \<value\> que describa el valor que representa la propiedad.  
  
## Sintaxis  
  
```  
<value>property-description</value>  
```  
  
#### Parámetros  
 `property-description`  
 Descripción de la propiedad.  
  
## Comentarios  
 Compile con el parámetro [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación y generar un archivo con ellos.  
  
## Ejemplo  
  
```  
// xml_value_tag.cpp  
// compile with: /LD /clr /doc  
// post-build command: xdcmake xml_value_tag.dll  
using namespace System;  
/// Text for class Employee.  
public ref class Employee {  
private:  
   String ^ name;  
   /// <value>Name accesses the value of the name data member</value>  
public:  
   property String ^ Name {  
      String ^ get() {  
         return name;   
      }  
      void set(String ^ i) {  
         name = i;  
      }  
   }  
};  
```  
  
## Vea también  
 [Documentación de XML](../ide/xml-documentation-visual-cpp.md)