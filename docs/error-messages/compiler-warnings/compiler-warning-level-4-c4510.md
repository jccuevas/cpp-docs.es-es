---
title: Advertencia del compilador (nivel 4) C4510
ms.date: 11/04/2016
f1_keywords:
- C4510
helpviewer_keywords:
- C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
ms.openlocfilehash: 80183e9f7ef17cbc37592f36eb8db1df2be94827
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221095"
---
# <a name="compiler-warning-level-4-c4510"></a>Advertencia del compilador (nivel 4) C4510

'class': no se pudo generar el constructor predeterminado

El compilador no puede generar un constructor predeterminado para la clase especificada y se ha creado ningún constructor definido por el usuario. No podrá crear objetos de este tipo.

Hay varias situaciones que impiden que el compilador genere un constructor predeterminado, incluidos:

- Un miembro de datos const.

- Un miembro de datos que es una referencia.

Deberá crear un constructor predeterminado definido por el usuario para la clase que inicializa a estos miembros.

El ejemplo siguiente genera C4510:

```
// C4510.cpp
// compile with: /W4
struct A {
   const int i;
   int &j;
   A& operator=( const A& ); // C4510 expected
   // uncomment the following line to resolve this C4510
   // A(int ii, int &jj) : i(ii), j(jj) {}
};   // C4510

int main() {
}
```