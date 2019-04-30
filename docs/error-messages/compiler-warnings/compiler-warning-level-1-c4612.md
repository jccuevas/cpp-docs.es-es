---
title: Advertencia del compilador (nivel 1) C4612
ms.date: 08/27/2018
f1_keywords:
- C4612
helpviewer_keywords:
- C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
ms.openlocfilehash: ed5458fc52c1c9c9f12187095e4658204613d1a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406371"
---
# <a name="compiler-warning-level-1-c4612"></a>Advertencia del compilador (nivel 1) C4612

> error en el nombre de archivo de inclusión

## <a name="remarks"></a>Comentarios

Esta advertencia se produce con **#pragma include_alias** cuando un nombre de archivo es incorrecto o falta.

Los argumentos para el **#pragma include_alias** instrucción puede utilizar el formulario de presupuesto ("*filename*") o corchetes angulares (\<*filename*>), pero ambos deben usar el mismo formato.

## <a name="example"></a>Ejemplo

```cpp
// C4612.cpp
// compile with: /W1 /LD
#pragma include_alias("StandardIO", <stdio.h>) // C4612
```