---
title: Advertencia del compilador (nivel 4) C4673
ms.date: 11/04/2016
f1_keywords:
- C4673
helpviewer_keywords:
- C4673
ms.assetid: 95626ec6-f05b-43c7-8b9a-a60a6f98dd30
ms.openlocfilehash: cd53aeb7f767b06c017c64caa55c916aa1e2b9c9
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990582"
---
# <a name="compiler-warning-level-4-c4673"></a>Advertencia del compilador (nivel 4) C4673

al iniciar ' Identifier ', los siguientes tipos no se tendrán en cuenta en el sitio Catch

No se puede controlar un objeto Throw en el bloque **catch** . Cada tipo que no se puede controlar aparece en la salida de error inmediatamente después de la línea que contiene esta advertencia. Cada tipo no controlado tiene su propia ADVERTENCIA. Lea la advertencia de cada tipo específico para obtener más información.

En el ejemplo siguiente se genera C4673:

```cpp
// C4673.cpp
// compile with: /EHsc /W4
class Base {
private:
   char * m_chr;
public:
   Base() {
      m_chr = 0;
   }

   ~Base() {
      if(m_chr)
         delete m_chr;
   }
};

class Derv : private Base {
public:
   Derv() {}
   ~Derv() {}
};

int main() {
   try {
      Derv D1;
      // delete previous line, uncomment the next line to resolve
      // Base D1;
      throw D1;   // C4673
   }

   catch(...) {}
}
```
