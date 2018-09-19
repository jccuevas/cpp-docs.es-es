---
title: Error del compilador C3550 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3550
dev_langs:
- C++
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 08c22d7e371fda7a229b541f78d4385f2943ee54
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047790"
---
# <a name="compiler-error-c3550"></a>Error del compilador C3550

solo se permite 'decltype(auto)' sin formato en este contexto

Si se usa `decltype(auto)` como marcador de posición para el tipo de valor devuelto de una función, debe usarse por sí mismo. No se puede usar como parte de una declaración de puntero (`decltype(auto*)`), una declaración de referencia (`decltype(auto&)`) o cualquier otra cualificación similar.

## <a name="see-also"></a>Vea también

[auto](../../cpp/auto-cpp.md)