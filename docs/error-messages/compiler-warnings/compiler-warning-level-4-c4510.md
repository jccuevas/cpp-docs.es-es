---
title: Compilador advertencia (nivel 4) C4510 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4510
dev_langs:
- C++
helpviewer_keywords:
- C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2aaf7286c2e900629a18d7df5824ef4b7af1f5f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048973"
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