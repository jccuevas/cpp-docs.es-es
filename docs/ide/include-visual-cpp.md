---
title: "&lt;include&gt; (Visual C++) | Microsoft Docs"
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
  - "include"
  - "<include>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<include> (etiqueta XML) [C++]"
  - "include (etiqueta XML) [C++]"
ms.assetid: 392a3e61-0371-4617-8362-446650876ce3
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;include&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La etiqueta \<include\> permite hacer referencia a comentarios colocados en otro archivo que describen los tipos y miembros del código fuente.  Ésta es una alternativa al método habitual de colocar los comentarios de la documentación directamente en el archivo de código fuente.  Por ejemplo, puede utilizar \<include\> para insertar comentarios estándar de “plancha de caldera” que se utilizan en el equipo o la compañía.  
  
## Sintaxis  
  
```  
<include file='filename' path='tagpath' />  
```  
  
#### Parámetros  
 `filename`  
 Nombre del archivo que contiene la documentación.  El nombre de archivo se puede completar con una ruta de acceso.  Agregue el nombre entre comillas simples o dobles.  El compilador emite una advertencia si no encuentra `filename`.  
  
 `tagpath`  
 Una expresión válida Xpath que selecciona deseado nodo\- establecido contenido en el archivo.  
  
 `name`  
 Especificador de nombre en la etiqueta que precede a los comentarios; `name` poseerá un `id`.  
  
 `id`  
 Identificador para la etiqueta que precede a los comentarios.  Agregue el nombre entre comillas simples o dobles.  
  
## Comentarios  
 La etiqueta \<include\> utiliza la sintaxis XPath de XML.  Consulte la documentación de Xpath para que las maneras personalicen utilizando \<include\>.  
  
 Compile con el parámetro [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación y generar un archivo con ellos.  
  
## Ejemplo  
 Este ejemplo utiliza varios archivos.  El primer archivo, que utiliza \<include\>, contiene los comentarios de documentación siguientes:  
  
```  
// xml_include_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_include_tag.dll  
  
/// <include file='xml_include_tag.doc' path='MyDocs/MyMembers[@name="test"]/*' />  
public ref class Test {  
   void TestMethod() {  
   }  
};  
  
/// <include file='xml_include_tag.doc' path='MyDocs/MyMembers[@name="test2"]/*' />  
public ref class Test2 {  
   void Test() {  
   }  
};  
```  
  
 El segundo archivo, xml\_include\_tag.doc, contiene los siguientes comentarios de documentación:  
  
```  
<MyDocs>  
  
<MyMembers name="test">  
<summary>  
The summary for this type.  
</summary>  
</MyMembers>  
  
<MyMembers name="test2">  
<summary>  
The summary for this other type.  
</summary>  
</MyMembers>  
  
</MyDocs>  
```  
  
## Resultado del programa  
  
```  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>t2</name>  
    </assembly>  
    <members>  
        <member name="T:Test">  
            <summary>  
The summary for this type.  
</summary>  
        </member>  
        <member name="T:Test2">  
            <summary>  
The summary for this other type.  
</summary>  
        </member>  
    </members>  
</doc>  
```  
  
## Vea también  
 [Documentación de XML](../ide/xml-documentation-visual-cpp.md)