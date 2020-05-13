---
title: en desuso (C++)
ms.date: 03/28/2017
f1_keywords:
- deprecated_cpp
helpviewer_keywords:
- __declspec keyword [C++], deprecated
- deprecated __declspec keyword
ms.assetid: beef1129-9434-4cb3-8392-f1eb29e04805
ms.openlocfilehash: e4689d3cb1a1757e2ac3bf4ca9eef7670ad5c655
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189486"
---
# <a name="deprecated-c"></a>en desuso (C++)

Este tema trata sobre la declaración de declspec obsoleto específica de Microsoft. Para obtener información sobre el atributo de `[[deprecated]]` de c++ 14, así como instrucciones sobre Cuándo usar ese atributo frente al declspec o pragma específico de Microsoft, vea [ C++ atributos estándar](attributes.md).

Con las excepciones que se indican a continuación, la declaración en **desuso** ofrece la misma funcionalidad que la pragma [desusada](../preprocessor/deprecated-c-cpp.md) :

- La declaración en **desuso** permite especificar formas determinadas de sobrecargas de función como desusadas, mientras que la forma pragma se aplica a todas las formas sobrecargadas de un nombre de función.

- La declaración en **desuso** permite especificar un mensaje que se mostrará en tiempo de compilación. El texto del mensaje puede proceder de una macro.

- Las macros solo se pueden marcar como desusadas con la pragma **desusada** .

Si el compilador encuentra el uso de un identificador en desuso o el atributo de [`[[deprecated]]`](attributes.md) estándar, se produce una advertencia [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) .

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo marcar funciones como desusadas y cómo especificar un mensaje que se mostrará, en tiempo de compilación, cuando se use la función desusada.

```cpp
// deprecated.cpp
// compile with: /W3
#define MY_TEXT "function is deprecated"
void func1(void) {}
__declspec(deprecated) void func1(int) {}
__declspec(deprecated("** this is a deprecated function **")) void func2(int) {}
__declspec(deprecated(MY_TEXT)) void func3(int) {}

int main() {
   func1();
   func1(1);   // C4996
   func2(1);   // C4996
   func3(1);   // C4996
}
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo marcar clases como desusadas y cómo especificar un mensaje que se mostrará, en tiempo de compilación, cuando se use la clase desusada.

```cpp
// deprecate_class.cpp
// compile with: /W3
struct __declspec(deprecated) X {
   void f(){}
};

struct __declspec(deprecated("** X2 is deprecated **")) X2 {
   void f(){}
};

int main() {
   X x;   // C4996
   X2 x2;   // C4996
}
```

## <a name="see-also"></a>Consulte también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
