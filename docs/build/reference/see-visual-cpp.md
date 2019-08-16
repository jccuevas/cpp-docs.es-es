---
title: '&lt;Consulte > (comentarios de documentación de C++)'
ms.date: 11/04/2016
f1_keywords:
- <see>
- see
helpviewer_keywords:
- <see> C++ XML tag
- see C++ XML tag
ms.assetid: 20ef66f4-b278-45cf-8613-63919edf5720
ms.openlocfilehash: be99d3ac156c587888a7c56997d82531cf86ccec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318906"
---
# <a name="ltseegt"></a>&lt;see&gt;

La etiqueta \<see> permite especificar un vínculo desde el texto. Use [\<seealso>](seealso-visual-cpp.md) para indicar el texto que quiere que aparezca en una sección Vea también.

## <a name="syntax"></a>Sintaxis

```
<see cref="member"/>
```

#### <a name="parameters"></a>Parámetros

*member*<br/>
Referencia a un miembro o campo al cual se puede llamar desde el entorno de compilación actual.  Ponga el nombre entre comillas simples o dobles.

El compilador comprueba si el elemento de código dado existe y resuelve `member` en el nombre de elemento en el resultado XML.  El compilador emite una advertencia si no encuentra `member`.

## <a name="remarks"></a>Comentarios

Compile con [/doc](doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación a un archivo.

Vea [\<summary>](summary-visual-cpp.md) para obtener un ejemplo del uso de \<see>.

El compilador de MSVC intentará resolver referencias cref en un paso a través de los comentarios de documentación.  Por tanto, si usa las reglas de búsqueda de C++, un símbolo que no encuentra el compilador se marcará como no resuelto. Vea [\<seealso>](seealso-visual-cpp.md) para obtener más información.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo puede hacer que cref haga referencia a un tipo genérico, de modo que el compilador resuelva la referencia.

```
// xml_see_cref_example.cpp
// compile with: /LD /clr /doc
// the following cref shows how to specify the reference, such that,
// the compiler will resolve the reference
/// <see cref="C{T}">
/// </see>
ref class A {};

// the following cref shows another way to specify the reference,
// such that, the compiler will resolve the reference
/// <see cref="C < T >"/>

// the following cref shows how to hard-code the reference
/// <see cref="T:C`1">
/// </see>
ref class B {};

/// <see cref="A">
/// </see>
/// <typeparam name="T"></typeparam>
generic<class T>
ref class C {};
```

## <a name="see-also"></a>Vea también

[Documentación de XML](xml-documentation-visual-cpp.md)
