---
title: '&lt;Incluir > (comentarios de documentación de C++)'
ms.date: 11/04/2016
f1_keywords:
- include
- <include>
helpviewer_keywords:
- include C++ XML tag
- <include> C++ XML tag
ms.assetid: 392a3e61-0371-4617-8362-446650876ce3
ms.openlocfilehash: b7d1033aa5b6c95c0db8eb9debf74596dc214fb0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291332"
---
# <a name="ltincludegt"></a>&lt;include&gt;

La etiqueta \<include> le permite hacer referencia a comentarios colocados en otro archivo que describen los tipos y miembros en el código fuente. Esto es una alternativa a colocar los comentarios de documentación directamente en el archivo de código fuente.  Por ejemplo, se puede usar \<include> para insertar comentarios estándar "reutilizables" que se usen en todo el equipo o la empresa.

## <a name="syntax"></a>Sintaxis

```
<include file='filename' path='tagpath' />
```

#### <a name="parameters"></a>Parámetros

*filename*<br/>
El nombre del archivo que contiene la documentación. El nombre de archivo se puede calificar con una ruta de acceso.  Ponga el nombre entre comillas simples o dobles.  El compilador emite una advertencia si no encuentra `filename`.

*tagpath*<br/>
Una expresión XPath válida que selecciona el conjunto de nodos deseado contenido en el archivo.

*name*<br/>
El especificador de nombre en la etiqueta que precede a los comentarios; `name` tendrá un `id`.

*identificador*<br/>
El identificador de la etiqueta que precede a los comentarios.  Ponga el nombre entre comillas simples o dobles.

## <a name="remarks"></a>Comentarios

La etiqueta \<include> usa la sintaxis de XPath de XML. Consulte la documentación de XPath para ver formas de personalización mediante \<include>.

Compile con [/doc](doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación a un archivo.

## <a name="example"></a>Ejemplo

Este es un ejemplo de múltiples archivos. El primer archivo, en el que se usa \<include>, contiene los comentarios de documentación siguientes:

```cpp
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

```xml
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

```xml
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

[Documentación de XML](xml-documentation-visual-cpp.md)
