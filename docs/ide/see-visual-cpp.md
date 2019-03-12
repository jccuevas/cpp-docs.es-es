---
title: '&lt;see&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- <see>
- see
helpviewer_keywords:
- <see> C++ XML tag
- see C++ XML tag
ms.assetid: 20ef66f4-b278-45cf-8613-63919edf5720
ms.openlocfilehash: c8e797dff1495e9b4573ab4e0820d60b8027a293
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747597"
---
# <a name="ltseegt-visual-c"></a>&lt;see&gt; (Visual C++)

La etiqueta \<see> permite especificar un vínculo desde el texto. Use [\<seealso>](../ide/seealso-visual-cpp.md) para indicar el texto que quiere que aparezca en una sección Vea también.

## <a name="syntax"></a>Sintaxis

```
<see cref="member"/>
```

#### <a name="parameters"></a>Parámetros

*member*<br/>
Referencia a un miembro o campo al cual se puede llamar desde el entorno de compilación actual.  Ponga el nombre entre comillas simples o dobles.

El compilador comprueba si el elemento de código dado existe y resuelve `member` en el nombre de elemento en el resultado XML.  El compilador emite una advertencia si no encuentra `member`.

## <a name="remarks"></a>Comentarios

Compile con [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación a un archivo.

Vea [\<summary>](../ide/summary-visual-cpp.md) para obtener un ejemplo del uso de \<see>.

El compilador de Visual C++ intentará resolver referencias cref en un paso por los comentarios de documentación.  Por tanto, si usa las reglas de búsqueda de C++, un símbolo que no encuentra el compilador se marcará como no resuelto. Vea [\<seealso>](../ide/seealso-visual-cpp.md) para obtener más información.

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

[Documentación de XML](../ide/xml-documentation-visual-cpp.md)
