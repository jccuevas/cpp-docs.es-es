---
title: Compilador advertencia (nivel 1) C4407 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4407
dev_langs:
- C++
helpviewer_keywords:
- C4407
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a9a665dbb71157b37f72d3d0721357d00dc37230
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032610"
---
# <a name="compiler-warning-level-1-c4407"></a>Advertencia del compilador (nivel 1) C4407

conversión entre diferentes representaciones de puntero a miembro, el compilador puede generar código incorrecto

Se detectó una conversión incorrecta.

C4407 pueden generarse debido a la del trabajo de conformidad del compilador efectuado en Visual C++ 2005. Puntero a miembro ahora requiere un nombre completo y el operador address-of (&).

C4407 puede producirse si puede convertir entre un varios herencia puntero a miembro a un herencia simple puntero a miembro. A veces esto puede funcionar, pero a veces no puede porque la representación de puntero a miembro de herencia única no contiene información suficiente. Compilar con la **/VMM** podría ayudar a (para obtener más información, consulte [/VMM, / VMs, /vmv (representación de propósito General)](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)). También puede intentar volver a organizar las clases base. el compilador detecta una pérdida de información en la conversión porque es una clase base con un desplazamiento distinto de cero de la clase derivada.

El ejemplo siguiente genera la advertencia C4407:

```
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