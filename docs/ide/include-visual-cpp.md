---
title: '&lt;incluir&gt; (Visual C++) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- include
- <include>
dev_langs: C++
helpviewer_keywords:
- include C++ XML tag
- <include> C++ XML tag
ms.assetid: 392a3e61-0371-4617-8362-446650876ce3
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f9a6b07ce540d67a44e46a24fb943dac93bb95a4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ltincludegt-visual-c"></a>&lt;incluir&gt; (Visual C++)
La etiqueta \<include> le permite hacer referencia a comentarios colocados en otro archivo que describen los tipos y miembros en el código fuente. Esto es una alternativa a colocar los comentarios de documentación directamente en el archivo de código fuente.  Por ejemplo, puede usar \<incluyen > para insertar comentarios estándar "reutilizable" que se utilizan a lo largo de su equipo o empresa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<include file='filename' path='tagpath' />  
```  
  
#### <a name="parameters"></a>Parámetros  
 `filename`  
 El nombre del archivo que contiene la documentación. El nombre de archivo se puede calificar con una ruta de acceso.  Ponga el nombre entre comillas simples o dobles.  El compilador emite una advertencia si no encuentra `filename`.  
  
 `tagpath`  
 Una expresión XPath válida que selecciona el conjunto de nodos deseado contenido en el archivo.  
  
 `name`  
 El especificador de nombre en la etiqueta que precede a los comentarios; `name` tendrá un `id`.  
  
 `id`  
 El identificador de la etiqueta que precede a los comentarios.  Ponga el nombre entre comillas simples o dobles.  
  
## <a name="remarks"></a>Comentarios  
 La etiqueta \<include> usa la sintaxis de XPath de XML. Consulte la documentación de XPath para formas de personalizar utilizando \<incluyen >.  
  
 Compile con [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación a un archivo.  
  
## <a name="example"></a>Ejemplo  
 Este es un ejemplo de múltiples archivos. El primer archivo, que utiliza \<incluyen >, contiene los siguientes comentarios de documentación:  
  
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
  
 El segundo archivo, xml_include_tag.doc, contiene los siguientes comentarios de documentación:  
  
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
  
## <a name="program-output"></a>Resultados del programa  
  
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
  
## <a name="see-also"></a>Vea también  
 [Documentación de XML](../ide/xml-documentation-visual-cpp.md)