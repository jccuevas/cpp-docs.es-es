---
title: '&lt;paramref > (C++ comentarios de documentación)'
ms.date: 11/04/2016
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- paramref C++ XML tag
- <paramref> C++ XML tag
ms.assetid: c5730dc2-7159-421f-b2d5-bb971e307122
ms.openlocfilehash: 1f4e9cb0e6b39e4da78e78048342dac2ecc9deea
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988689"
---
# <a name="ltparamrefgt"></a>&lt;paramref&gt;

La etiqueta \<paramref> ofrece una manera de indicar que una palabra es un parámetro. El archivo .xml se puede procesar para dar formato a este parámetro de una forma exclusiva.

## <a name="syntax"></a>Sintaxis

```
<paramref name="name"/>
```

#### <a name="parameters"></a>Parameters

*name*<br/>
Nombre del parámetro al que se hace referencia.  Ponga el nombre entre comillas simples o dobles.  El compilador emite una advertencia si no encuentra `name`.

## <a name="remarks"></a>Notas

Compile con el parámetro [/doc](doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación y generar un archivo con ellos.

## <a name="example"></a>Ejemplo

```cpp
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
