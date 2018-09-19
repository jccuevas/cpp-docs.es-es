---
title: Error del compilador C2552 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2552
dev_langs:
- C++
helpviewer_keywords:
- C2552
ms.assetid: 0e0ab759-788a-4faf-9337-80d4b9e2e8c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5f54d9bf40c2dda7de0d7f518813e661b0476caa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044306"
---
# <a name="compiler-error-c2552"></a>Error del compilador C2552

“identificador”: los no agregados no se pueden inicializar con la lista de inicializadores

El identificador de agregado se inicializó incorrectamente.

[Agregados](../../c-language/initializing-aggregate-types.md) se definen como:

- Matrices

- Clases, estructuras y uniones que no tienen:

   - Constructores

   - Miembros privados o protegidos

   - Clases base

   - Funciones virtuales

Además, Visual C++ no permite los tipos de datos en un agregado que contiene constructores.

Las siguientes son las razones por las que C2552 puede desencadenarse cuando se intenta una inicialización de agregado en un tipo:

- El tipo tiene uno o varios constructores definidos por el usuario.

- El tipo tiene uno o varios miembros de datos privados no estáticos.

- El tipo tiene una o varias funciones virtuales.

- El tipo tiene una clase base.

- Un tipo es una clase ref o una interfaz CLR.

- El tipo tiene una matriz de dimensión no fija (matriz cero) cuyos elementos tienen destructores.

El código siguiente genera el error C2552:

```
// C2552.cpp
// compile with: /clr
#include <string>
using namespace std;

struct Pair_Incorrect {
private:
   string m_name;
   double m_val;
};

struct Pair_Correct1 {
public:
   Pair_Correct1(string name, double val)
      : m_name(name), m_val(val) {}

private:
   string m_name;
   double m_val;
};

struct Pair_Correct2 {
public:
   string m_name;
   double m_val;
};

int main() {
   // To fix, add a constructor to this class and use it for
   // initializing the data members, see Pair_Correct1 (below)
   // or
   // Do not have any private or protected non-static data members,
   // see Pair_Correct2 (below).  Pair_Correct2 is not recommended in
   // case your object model requires some non-static data members to
   // be private or protected

   string name("John");
   Pair_Incorrect pair1 = { name, 0.0 };   // C2552

   // initialize a CLR immutable value type that has a constructor
   System::DateTime dt = {2001, 4, 12, 22, 16, 49, 844};   // C2552

   Pair_Correct1 pair2( name, 0.0 );
   Pair_Correct1 pair3 = Pair_Correct1( name, 0.0 );
   Pair_Correct2 pair4 = { name, 0.0 };
   System::DateTime dt2(2001, 4, 12, 22, 16, 49, 844);
}
```