---
title: Compilador advertencia (nivel 3) C4023 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4023
dev_langs:
- C++
helpviewer_keywords:
- C4023
ms.assetid: 615d5374-d7c1-42eb-acfd-917c053270c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fe457f9a6181fa11b34dd615ad4d5b9637c8bddc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045177"
---
# <a name="compiler-warning-level-3-c4023"></a>Advertencia del compilador (nivel 3) C4023

'símbolo': el puntero con base se pasó a la función sin prototipo: número de parámetro

Si se pasa un puntero con base a una función sin prototipo, el puntero se normaliza, con resultados imprevisibles.

Para resolver esta advertencia, use funciones prototipo a las que se pasan punteros con base.