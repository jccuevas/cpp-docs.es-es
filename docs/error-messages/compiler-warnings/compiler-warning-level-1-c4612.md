---
title: Compilador advertencia (nivel 1) C4612 | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4612
dev_langs:
- C++
helpviewer_keywords:
- C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 10a0a5640386f5e5673f39d6c2c76ee18fcc7ba7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210735"
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