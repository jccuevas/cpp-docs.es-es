---
title: "&lt;param&gt; (Visual C++) | Microsoft Docs"
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
  - "param"
  - "<param>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<param> (etiqueta XML) [C++]"
  - "param (etiqueta XML) [C++]"
ms.assetid: 66c1a1c3-4f98-4bcf-8c7d-9a40308982fb
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;param&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La etiqueta \<param\> se debe utilizar en el comentario de una declaración de método para describir uno de los parámetros del método.  
  
## Sintaxis  
  
```  
<param name='name'>description</param>  
```  
  
#### Parámetros  
 `name`  
 Nombre de un parámetro de método.  Agregue el nombre entre comillas simples o dobles.  El compilador emite una advertencia si no encuentra `name`.  
  
 `description`  
 Descripción del parámetro.  
  
## Comentarios  
 El texto de la etiqueta de \<param\> se mostrará en IntelliSense, [Examinador de objetos](http://msdn.microsoft.com/es-es/f89acfc5-1152-413d-9f56-3dc16e3f0470)y, en el informe web de comentarios de código.  
  
 Compile con el parámetro [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación y generar un archivo con ellos.  
  
## Ejemplo  
  
```  
// xml_param_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_param_tag.dll  
/// Text for class MyClass.  
public ref class MyClass {  
   /// <param name="Int1">Used to indicate status.</param>  
   void MyMethod(int Int1) {  
   }  
};  
```  
  
## Vea también  
 [Documentación de XML](../ide/xml-documentation-visual-cpp.md)