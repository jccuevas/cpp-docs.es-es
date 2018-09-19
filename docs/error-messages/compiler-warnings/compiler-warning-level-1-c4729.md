---
title: Compilador advertencia (nivel 1) C4729 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4729
dev_langs:
- C++
helpviewer_keywords:
- C4729
ms.assetid: 36a0151f-f258-48d9-9444-ae6d41ff70a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7d1f5b4fe452937ce74e56886a5214ff92f44af7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096085"
---
# <a name="compiler-warning-level-1-c4729"></a>Advertencia del compilador (nivel 1) C4729

función demasiado grande para advertencias basadas en gráficos de flujos

Esta advertencia se genera cuando una función es demasiado grande para compilarse con una comprobación confiable en situaciones que generarían una advertencia. Esta advertencia solo se genera cuando se utiliza la opción del compilador [/Od](../../build/reference/od-disable-debug.md) .

Para resolver esta advertencia, divida la función en funciones más pequeñas.