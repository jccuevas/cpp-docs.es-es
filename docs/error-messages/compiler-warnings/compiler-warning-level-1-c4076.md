---
title: Advertencia del compilador (nivel 1) C4076
ms.date: 11/04/2016
f1_keywords:
- C4076
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
ms.openlocfilehash: 3a56e58d9bec1034a55f4e588dbddd0dba03f348
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437029"
---
# <a name="compiler-warning-level-1-c4076"></a>Advertencia del compilador (nivel 1) C4076

> '*modificador de tipo*': no se puede usar con el tipo '*typename*'

## <a name="remarks"></a>Comentarios

Un modificador de tipo, ya sea **firmado** o **sin signo**, no se puede usar con un tipo no entero. *modificador de tipo* se omite.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4076; Para corregirlo, quite el **sin signo** modificador de tipo:

```cpp
// C4076.cpp
// compile with: /W1 /LD
unsigned double x;   // C4076
```