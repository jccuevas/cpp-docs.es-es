---
title: "&lt;summary&gt; (Visual C++) | Microsoft Docs"
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
  - "<summary>"
  - "summary"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<summary> (etiqueta XML) [C++]"
  - "summary (etiqueta XML) [C++]"
ms.assetid: cdeeefbb-1339-45d6-9002-10042a9a2726
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;summary&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La etiqueta \<summary\> se utiliza para describir un tipo o un miembro de tipo.  Utilice [\<remarks\>](../ide/remarks-visual-cpp.md) para suministrar información adicional a una descripción de tipo.  
  
## Sintaxis  
  
```  
<summary>description</summary>  
```  
  
#### Parámetros  
 `description`  
 Resumen del objeto.  
  
## Comentarios  
 El texto de la etiqueta de \<summary\> es la única fuente de información sobre el tipo en IntelliSense, y se muestra en [Examinador de objetos](http://msdn.microsoft.com/es-es/f89acfc5-1152-413d-9f56-3dc16e3f0470) y en el informe web de comentarios de código.  
  
 Compile con el parámetro [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación y generar un archivo con ellos.  
  
## Ejemplo  
  
```  
// xml_summary_tag.cpp  
// compile with: /LD /clr /doc  
// post-build command: xdcmake xml_summary_tag.dll  
  
/// Text for class MyClass.  
public ref class MyClass {  
public:  
   /// <summary>MyMethod is a method in the MyClass class.  
   /// <para>Here's how you could make a second paragraph in a description. <see cref="System::Console::WriteLine"/> for information about output statements.</para>  
   /// <seealso cref="MyClass::MyMethod2"/>  
   /// </summary>  
   void MyMethod(int Int1) {}  
  
   /// text  
   void MyMethod2() {}  
};  
```  
  
## Vea también  
 [Documentación de XML](../ide/xml-documentation-visual-cpp.md)