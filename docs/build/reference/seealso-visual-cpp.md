---
title: '&lt;seealso > (comentarios de documentación de C++)'
ms.date: 11/04/2016
f1_keywords:
- <seealso>
- seealso
helpviewer_keywords:
- seealso C++ XML tag
- <seealso> C++ XML tag
ms.assetid: cb33d100-9c50-4485-8d0c-573429eff155
ms.openlocfilehash: ea399e98723a265ef3c17f2282b7c81299b4abc5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318841"
---
# <a name="ltseealsogt"></a>&lt;seealso&gt;

La etiqueta \<seealso> le permite especificar el texto que quiere que aparezca en una sección Vea también. Use [\<see>](see-visual-cpp.md) para especificar un vínculo desde dentro del texto.

## <a name="syntax"></a>Sintaxis

```
<seealso cref="member"/>
```

#### <a name="parameters"></a>Parámetros

*member*<br/>
Referencia a un miembro o campo al cual se puede llamar desde el entorno de compilación actual.  Ponga el nombre entre comillas simples o dobles.

El compilador comprueba si el elemento de código dado existe y resuelve `member` en el nombre de elemento en el resultado XML.  El compilador emite una advertencia si no encuentra `member`.

Para obtener información sobre cómo crear una referencia cref a un tipo genérico, vea [\<see>](see-visual-cpp.md).

## <a name="remarks"></a>Comentarios

Compile con [/doc](doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación a un archivo.

Vea [\<summary>](summary-visual-cpp.md) para obtener un ejemplo del uso de \<seealso>.

El compilador de MSVC intentará resolver referencias cref en un paso a través de los comentarios de documentación.  Por tanto, si usa las reglas de búsqueda de C++, un símbolo que no encuentra el compilador se marcará como no resuelto.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente, se hace referencia a un símbolo sin resolver en cref. El comentario XML para el cref de B::Test será `<seealso cref="!:B::Test" />`, mientras que la referencia a A::Test es `<seealso cref="M:A.Test" />` bien formada.

```
// xml_seealso_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_seealso_tag.dll

/// Text for class A.
public ref struct A {
   /// <summary><seealso cref="A::Test"/>
   /// <seealso cref="B::Test"/>
   /// </summary>
   void MyMethod(int Int1) {}

   /// text
   void Test() {}
};

/// Text for class B.
public ref struct B {
   void Test() {}
};
```

## <a name="see-also"></a>Vea también

[Documentación de XML](xml-documentation-visual-cpp.md)
