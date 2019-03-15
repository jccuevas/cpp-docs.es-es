---
title: '&lt;paramref > (comentarios de documentación de C++)'
ms.date: 11/04/2016
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- paramref C++ XML tag
- <paramref> C++ XML tag
ms.assetid: c5730dc2-7159-421f-b2d5-bb971e307122
ms.openlocfilehash: cee35ddb5fd5cd811e45f0aa49e94dd9c4b8b180
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826774"
---
# <a name="ltparamrefgt"></a>&lt;paramref&gt;

La etiqueta \<paramref> ofrece una manera de indicar que una palabra es un parámetro. El archivo .xml se puede procesar para dar formato a este parámetro de una forma exclusiva.

## <a name="syntax"></a>Sintaxis

```
<paramref name="name"/>
```

#### <a name="parameters"></a>Parámetros

*name*<br/>
Nombre del parámetro al que se hace referencia.  Ponga el nombre entre comillas simples o dobles.  El compilador emite una advertencia si no encuentra `name`.

## <a name="remarks"></a>Comentarios

Compile con [/doc](doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación a un archivo.

## <a name="example"></a>Ejemplo

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

## <a name="see-also"></a>Vea también

[Documentación de XML](xml-documentation-visual-cpp.md)
