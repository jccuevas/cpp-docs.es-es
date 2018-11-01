---
title: Advertencia del compilador (nivel 4) C4611
ms.date: 11/04/2016
f1_keywords:
- C4611
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
ms.openlocfilehash: b799c568d73a081a4d4cf5616f376f3efc9eeffb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50542316"
---
# <a name="compiler-warning-level-4-c4611"></a>Advertencia del compilador (nivel 4) C4611

interacción entre 'función' y la destrucción de objetos de C++ no es transportable

En algunas plataformas, las funciones que incluyen **catch** pueden no admitir la semántica de destrucción cuando fuera del ámbito de objeto de C++.

Para evitar un comportamiento inesperado, evite el uso de **catch** en funciones que tienen constructores y destructores.

Esta advertencia solo se emite una vez. consulte [advertencia pragma](../../preprocessor/warning.md).