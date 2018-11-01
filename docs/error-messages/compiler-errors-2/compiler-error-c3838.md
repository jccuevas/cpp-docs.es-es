---
title: Error del compilador C3838
ms.date: 11/04/2016
f1_keywords:
- C3838
helpviewer_keywords:
- C3838
ms.assetid: d6f470c2-131a-4a8c-843a-254acd43da83
ms.openlocfilehash: c8664c9df837d44ab6e356d54ff9e35c3776778a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635232"
---
# <a name="compiler-error-c3838"></a>Error del compilador C3838

no se puede heredar explícitamente de 'type'

Especificado `type` no puede actuar como clase base en cualquier clase.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3838:

```
// C3838a.cpp
// compile with: /clr /c
public ref class B : public System::Enum {};   // C3838
```
