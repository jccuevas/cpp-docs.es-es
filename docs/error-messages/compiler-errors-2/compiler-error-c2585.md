---
title: Error del compilador C2585 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2585
dev_langs:
- C++
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ec7b1e9c1e5e7894740cc80f9c030fa1ee26ec0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028849"
---
# <a name="compiler-error-c2585"></a>Error del compilador C2585

conversión explícita a 'type' es ambigua

El tipo de conversión puede producir más de un resultado.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Convertir un tipo de clase o estructura en función de herencia múltiple. Si el tipo hereda la misma clase base más de una vez, la función de conversión o un operador debe utilizar la resolución de ámbito (`::`) para especificar cuál de las clases heredadas a usar en la conversión.

1. Se ha definido un operador de conversión y un constructor que hace la misma conversión.