---
title: Error del compilador C2803 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2803
dev_langs:
- C++
helpviewer_keywords:
- C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7885735ebad1ff90afaf4ba8eaf6dfca9f3e0ab3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027046"
---
# <a name="compiler-error-c2803"></a>Error del compilador C2803

'operator operator' debe tener al menos un parámetro formal de tipo de clase

El operador sobrecargado no tiene un parámetro de tipo de clase.

Debe pasar al menos un parámetro por referencia (que no usan punteros, pero las referencias) o por valor para poder escribir "un < b" (un y b es de una clase de tipo A).

Si ambos parámetros son punteros será una comparación de direcciones de puntero pura y no utiliza la conversión definida por el usuario.

El ejemplo siguiente genera C2803:

```
// C2803.cpp
// compile with: /c
class A{};
bool operator< (const A *left, const A *right);   // C2803
// try the following line instead
// bool operator< (const A& left, const A& right);
```