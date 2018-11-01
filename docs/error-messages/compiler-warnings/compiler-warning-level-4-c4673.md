---
title: Advertencia del compilador (nivel 4) C4673
ms.date: 11/04/2016
f1_keywords:
- C4673
helpviewer_keywords:
- C4673
ms.assetid: 95626ec6-f05b-43c7-8b9a-a60a6f98dd30
ms.openlocfilehash: ceaa5cd647dfb527713613b9ce3b5cd81a780fd7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657735"
---
# <a name="compiler-warning-level-4-c4673"></a>Advertencia del compilador (nivel 4) C4673

produce los siguientes tipos de 'identifier' no se considerará en el bloque catch

Un objeto throw no puede controlarse en el **catch** bloque. Cada tipo que no se puede controlar se muestra en la salida de error inmediatamente después de la línea que contiene esta advertencia. Cada tipo no controlado tiene su propia advertencia. Lea la advertencia para cada tipo específico para obtener más información.

El ejemplo siguiente genera C4673:

```
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