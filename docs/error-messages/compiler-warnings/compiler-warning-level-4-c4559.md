---
title: Compilador advertencia (nivel 4) C4559 | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4559
dev_langs:
- C++
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d5743b33f62aa954c3765b729ab5c0297b20e32
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195581"
---
# <a name="compiler-warning-level-4-c4559"></a>Advertencia del compilador (nivel 4) C4559

> '*función*': redefinición; el __declspec ganancias de función (*modificador*)

## <a name="remarks"></a>Comentarios

Una función volvió a definir o declarar de nuevo y la segunda definición o declaración agrega un **__declspec** modificador (*modificador*). La advertencia es informativa. Para corregir esta advertencia, elimine una de las definiciones.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4559:

```cpp
// C4559.cpp
// compile with: /W4 /LD
void f();
__declspec(noalias) void f();   // C4559
```