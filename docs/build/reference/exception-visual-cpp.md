---
title: '&lt;> de excepcionesC++ (comentarios de documentación)'
ms.date: 11/04/2016
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C++ XML tag
- exception C++ XML tag
ms.assetid: 24451e79-9b89-4b77-98fb-702c6516b818
ms.openlocfilehash: ddfe647fa2db55b3ca606265011896a66398a8a2
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988293"
---
# <a name="ltexceptiongt"></a>&lt;exception&gt;

La etiqueta \<exception> le permite especificar qué excepciones se pueden producir. Esta etiqueta se aplica a una definición de método.

## <a name="syntax"></a>Sintaxis

```
<exception cref="member">description</exception>
```

#### <a name="parameters"></a>Parameters

*member*<br/>
Una referencia a una excepción que está disponible desde el entorno de compilación actual. Mediante reglas de búsqueda de nombres, el compilador comprueba si la excepción dada existe y traduce `member` al nombre de elemento canónico en la salida XML.  El compilador emite una advertencia si no encuentra `member`.

Ponga el nombre entre comillas simples o dobles.

Para obtener información sobre cómo crear una referencia cref a un tipo genérico, vea [\<see>](see-visual-cpp.md).

*description*<br/>
Una descripción.

## <a name="remarks"></a>Notas

Compile con el parámetro [/doc](doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación y generar un archivo con ellos.

El compilador MSVC intentará resolver las referencias CREF en un paso a través de los comentarios de documentación.  Por tanto, si usa las reglas de búsqueda de C++, un símbolo que no encuentra el compilador se marcará como no resuelto. Vea [\<seealso>](seealso-visual-cpp.md) para obtener más información.

## <a name="example"></a>Ejemplo

```cpp
// xml_exception_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_exception_tag.dll
using namespace System;

/// Text for class EClass.
public ref class EClass : public Exception {
   // class definition ...
};

/// <exception cref="System.Exception">Thrown when... .</exception>
public ref class TestClass {
   void Test() {
      try {
      }
      catch(EClass^) {
      }
   }
};
```

## <a name="see-also"></a>Vea también

[Documentación de XML](xml-documentation-visual-cpp.md)
