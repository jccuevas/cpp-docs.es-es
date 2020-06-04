---
title: Advertencia del compilador (nivel 3) C4580
ms.date: 11/04/2016
f1_keywords:
- C4580
helpviewer_keywords:
- C4580
ms.assetid: fef6e8e0-0d6a-44fa-b22a-2fe7ba2ef379
ms.openlocfilehash: 28d8534dad5fc1b234c180b879ad0645f05cfd65
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198619"
---
# <a name="compiler-warning-level-3-c4580"></a>Advertencia del compilador (nivel 3) C4580

[attribute] está desusado; especifique en su lugar System::Attribute o Platform::Metadata como clase base

[[Attribute](../../windows/attributes/attribute.md)] ya no es la sintaxis preferida para crear atributos definidos por el usuario. Para obtener más información, consulte [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md). Para el código CLR, derive los atributos de `System::Attribute`. Para el código Windows en tiempo de ejecución, derive los atributos de `Platform::Metadata`.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera el error C3454 y se muestra cómo corregirlo:

```cpp
// C4580.cpp
// compile with: /W3 /c /clr
[attribute]   // C4580
public ref class Attr {
public:
   int m_t;
};

public ref class Attr2 : System::Attribute {
public:
   int m_t;
};
```
