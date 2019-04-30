---
title: Error del compilador C2140
ms.date: 11/04/2016
f1_keywords:
- C2140
helpviewer_keywords:
- C2140
ms.assetid: d44a0500-002c-4632-9e5e-c71c3a473ec4
ms.openlocfilehash: 35b6e38290acddb41bdf53d9663a058259300ee8
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345688"
---
# <a name="compiler-error-c2140"></a>Error del compilador C2140

'type': no se permite un tipo que depende de un parámetro de tipo genérico como argumento para el rasgo de tipo intrínseco 'rasgo'

Un especificador de tipo no válido se pasó un rasgo de tipo.

Para obtener más información, consulte [compatibilidad de compilador para Type Traits](../../extensions/compiler-support-for-type-traits-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2140.

```
// C2140.cpp
// compile with: /clr /c
template <class T>

struct is_polymorphic {
   static const bool value = __is_polymorphic(T);
};

class x {};

generic <class T>
ref class C {
   void f() {
      System::Console::WriteLine(__is_polymorphic(T));   // C2140
      System::Console::WriteLine(is_polymorphic<T>::value);   // C2140

      System::Console::WriteLine(__is_polymorphic(x));   // OK
      System::Console::WriteLine(is_polymorphic<x>::value);   // OK
   }
};
```