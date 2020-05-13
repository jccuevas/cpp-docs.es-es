---
title: Advertencia del compilador (nivel 1) C4407
ms.date: 11/04/2016
f1_keywords:
- C4407
helpviewer_keywords:
- C4407
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
ms.openlocfilehash: 8dd78872d4edf82fb61c8ab93639dbcd93085754
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162548"
---
# <a name="compiler-warning-level-1-c4407"></a>Advertencia del compilador (nivel 1) C4407

conversión entre diferentes representaciones de puntero a miembro, el compilador puede generar código incorrecto

Se detectó una conversión incorrecta.

Se puede generar C4407 debido al trabajo de conformidad del compilador realizado en Visual Studio 2005. El puntero a miembro ahora requiere un nombre completo y el operador Address-of (&).

C4407 puede producirse si se realiza la conversión entre un puntero a miembro de herencia múltiple y un puntero a miembro de herencia única. A veces, esto puede funcionar, pero a veces no puede hacerlo porque la representación de un solo puntero a miembro de herencia no contiene información suficiente. Compilar con **/VMM** puede ser de ayuda (para obtener más información, vea [/VMM,/VMS,/vmv (representación de uso general)](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)). También puede intentar reorganizar las clases base; el compilador está detectando una pérdida de información en la conversión porque una clase base está en un desplazamiento distinto de cero del derivado.

En el ejemplo siguiente se genera C4407:

```cpp
// C4407.cpp
// compile with: /W1 /c
struct C1 {};
struct C2 {};
struct C3 : C1, C2 {};

typedef void(C3::*PMF_C3)();
typedef void(C2::*PMF_C2)();

PMF_C2 f1(PMF_C3 pmf) {
   return (PMF_C2)pmf;   // C4407, change type of cast,
   // or reverse base class inheritance of C3 (i.e. : C2, C1)
}
```
