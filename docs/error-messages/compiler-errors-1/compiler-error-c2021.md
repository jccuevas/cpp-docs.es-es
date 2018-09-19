---
title: Error del compilador C2021 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2021
dev_langs:
- C++
helpviewer_keywords:
- C2021
ms.assetid: 064f32e2-3794-48d5-9767-991003dcb36a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31169c59ba9731d8eda52f22644294b8bb680bf2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102005"
---
# <a name="compiler-error-c2021"></a>Error del compilador C2021

se esperaba un valor de exponente, no 'character'

El carácter utilizado como exponente de una constante de punto flotante no es un número válido. Asegúrese de utilizar a un exponente que esté dentro del alcance.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2021:

```
// C2021.cpp
float test1=1.175494351E;   // C2021
```

## <a name="example"></a>Ejemplo

Posible resolución:

```
// C2021b.cpp
// compile with: /c
float test2=1.175494351E8;
```