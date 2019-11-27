---
title: Advertencia del compilador (nivel 3) C4641
ms.date: 11/04/2016
f1_keywords:
- C4641
helpviewer_keywords:
- C4641
ms.assetid: 28fe5c3e-6039-42da-9100-1312b5b15aea
ms.openlocfilehash: 0a930490f7b53fbbb31abb0f621cf972295d2ea6
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2019
ms.locfileid: "74189423"
---
# <a name="compiler-warning-level-3-c4641"></a>Advertencia del compilador (nivel 3) C4641

el comentario del documento XML tiene una referencia cruzada ambigua

El compilador no pudo resolver de forma inequívoca una referencia. Para resolver esta advertencia, especifique la información de parámetros necesaria para que la referencia no sea ambigua.

Para obtener más información, consulta [XML Documentation](../../build/reference/xml-documentation-visual-cpp.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4641.

```cpp
// C4641.cpp
// compile with: /W3 /doc /clr /c

/// <see cref="f" />   // C4641
// try the following line instead
// /// <see cref="f(int)" />
public ref class GR {
public:
   void f( int ) {}
   void f( char ) {}
};
```