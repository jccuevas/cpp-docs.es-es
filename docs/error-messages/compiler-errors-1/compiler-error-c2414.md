---
title: Error del compilador C2414 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2414
dev_langs:
- C++
helpviewer_keywords:
- C2414
ms.assetid: bbe94e03-862e-4990-b15e-544ae464727d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 642cb00605ed13146288edf5d39cb5d0c14c6e9f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089923"
---
# <a name="compiler-error-c2414"></a>Error del compilador C2414

número de operandos no válido

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. El código de operación no admite el número de operandos utilizado. Revise el manual de referencia del lenguaje de ensamblado para determinar el número correcto de operandos.

1. Un procesador más reciente admite la instrucción con un número diferente de operandos. Ajustar el [/arch (arquitectura de CPU mínima)](../../build/reference/arch-minimum-cpu-architecture.md) opción para usar el procesador más reciente.