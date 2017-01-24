---
title: "&lt;paramref&gt; (Visual C++) | Microsoft Docs"
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
  - "paramref"
  - "<paramref>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<paramref> (etiqueta XML) [C++]"
  - "paramref (etiqueta XML) [C++]"
ms.assetid: c5730dc2-7159-421f-b2d5-bb971e307122
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;paramref&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La etiqueta de \<paramref\> proporciona una forma de indicar que una palabra es un parámetro.  El archivo .xml se puede procesar para dar formato a este parámetro de alguna manera distinta.  
  
## Sintaxis  
  
```  
<paramref name="name"/>  
```  
  
#### Parámetros  
 `name`  
 Nombre del parámetro al que hay que hacer referencia.  Agregue el nombre entre comillas simples o dobles.  El compilador emite una advertencia si no encuentra `name`.  
  
## Comentarios  
 Compile con el parámetro [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación y generar un archivo con ellos.  
  
## Ejemplo  
  
```  
// xml_paramref_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_paramref_tag.dll  
/// Text for class MyClass.  
public ref class MyClass {  
   /// <summary>MyMethod is a method in the MyClass class.  
   /// The <paramref name="Int1"/> parameter takes a number.  
   /// </summary>  
   void MyMethod(int Int1) {}  
};  
```  
  
## Vea también  
 [Documentación de XML](../ide/xml-documentation-visual-cpp.md)