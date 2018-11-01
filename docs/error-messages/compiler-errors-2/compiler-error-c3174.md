---
title: Error del compilador C3174
ms.date: 11/04/2016
f1_keywords:
- C3174
helpviewer_keywords:
- C3174
ms.assetid: fe6b3b5a-8196-485f-a45f-0b2e51df4086
ms.openlocfilehash: 32f39eb1d808ccedd27ae3e4d343b87ddfde1862
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666354"
---
# <a name="compiler-error-c3174"></a>Error del compilador C3174

no se especificó el atributo de módulo

Un programa que utiliza atributos de Visual C++ no utilizó el [módulo](../../windows/module-cpp.md) atributo, que se requiere en cualquier programa que utiliza atributos.

El ejemplo siguiente genera C3174:

```
// C3174.cpp
// C3174 expected
// uncomment the following line to resolve this C3174
// [module(name="x")];
[export]
struct S
{
   int i;
};

int main()
{
}
```