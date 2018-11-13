---
title: '&lt;c&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- <c>
helpviewer_keywords:
- <c> C++ XML tag
- c C++ XML tag
ms.assetid: 3b23fc0f-e10d-4dd0-b197-48a46cbddd9f
ms.openlocfilehash: 1efb411537e07ae9a5c2e4a70b5fa3ac319d79c3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431101"
---
# <a name="ltcgt-visual-c"></a>&lt;c&gt; (Visual C++)

La etiqueta \<c> indica que el texto dentro de una descripción se debe marcar como código. Use [\<code>](../ide/code-visual-cpp.md) para indicar varias líneas como código.

## <a name="syntax"></a>Sintaxis

```
<c>text</c>
```

#### <a name="parameters"></a>Parámetros

*texto*<br/>
El texto que se quiere indicar como código.

## <a name="remarks"></a>Comentarios

Compile con [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación a un archivo.

## <a name="example"></a>Ejemplo

```cpp
// xml_c_tag.cpp
// compile with: /doc /LD
// post-build command: xdcmake xml_c_tag.xdc

/// Text for class MyClass.
class MyClass {
public:
   int m_i;
   MyClass() : m_i(0) {}

   /// <summary><c>MyMethod</c> is a method in the <c>MyClass</c> class.
   /// </summary>
   int MyMethod(MyClass * a) {
      return a -> m_i;
   }
};
```

## <a name="see-also"></a>Vea también

[Documentación de XML](../ide/xml-documentation-visual-cpp.md)