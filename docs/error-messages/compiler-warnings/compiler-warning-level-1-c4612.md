---
title: Advertencia del compilador (nivel 1) C4612
ms.date: 08/27/2018
f1_keywords:
- C4612
helpviewer_keywords:
- C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
ms.openlocfilehash: f9478caef9eaba9c72dc282179100daf2d94c6d5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185989"
---
# <a name="compiler-warning-level-1-c4612"></a>Advertencia del compilador (nivel 1) C4612

> error en el nombre de archivo de inclusión

## <a name="remarks"></a>Observaciones

Esta advertencia se produce con **#pragma include_alias** cuando un nombre de archivo es incorrecto o falta.

Los argumentos de la instrucción **#pragma include_alias** pueden usar el formulario de Comillas ("*filename*") o el formato de corchete angular (\<*nombre de archivo*>), pero ambos deben usar el mismo formato.

## <a name="example"></a>Ejemplo

```cpp
// C4612.cpp
// compile with: /W1 /LD
#pragma include_alias("StandardIO", <stdio.h>) // C4612
```
