---
title: '&lt;c > (comentarios de documentación de C++)'
ms.date: 11/04/2016
f1_keywords:
- <c>
helpviewer_keywords:
- <c> C++ XML tag
- c C++ XML tag
ms.assetid: 3b23fc0f-e10d-4dd0-b197-48a46cbddd9f
ms.openlocfilehash: 43e1417e5a749f2ea51346bbf6db235ba08a7bcf
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826614"
---
# <a name="ltcgt"></a>&lt;c&gt;

La etiqueta \<c> indica que el texto dentro de una descripción se debe marcar como código. Use [\<code>](code-visual-cpp.md) para indicar varias líneas como código.

## <a name="syntax"></a>Sintaxis

```
<c>text</c>
```

#### <a name="parameters"></a>Parámetros

*texto*<br/>
El texto que se quiere indicar como código.

## <a name="remarks"></a>Comentarios

Compile con [/doc](doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación a un archivo.

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

[Documentación de XML](xml-documentation-visual-cpp.md)
