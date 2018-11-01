---
title: Advertencia del compilador (nivel 3) C4306
ms.date: 08/27/2018
f1_keywords:
- C4306
helpviewer_keywords:
- C4306
ms.assetid: 5b2192d7-402d-4b6d-8619-08105e7dcac7
ms.openlocfilehash: 78ec291b555838b1af63287e3d24fdb809afd7c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582031"
---
# <a name="compiler-warning-level-3-c4306"></a>Advertencia del compilador (nivel 3) C4306

> '*identificador*': conversión de '*type1*'para'*type2*' de mayor tamaño

El identificador es de tipo en un puntero de mayor tamaño. Los bits superiores sin relleno del nuevo tipo será rellenan con ceros.

Esta advertencia puede indicar una conversión no deseada. El puntero resultante puede no ser válido.