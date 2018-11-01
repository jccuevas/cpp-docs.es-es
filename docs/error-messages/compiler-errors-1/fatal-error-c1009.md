---
title: Error irrecuperable C1009
ms.date: 11/04/2016
f1_keywords:
- C1009
helpviewer_keywords:
- C1009
ms.assetid: dcc8383c-3362-4c47-9c26-25d2451ebd53
ms.openlocfilehash: c4654d37f5ce184f6fa5b8888e6ca0184267be07
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50542667"
---
# <a name="fatal-error-c1009"></a>Error irrecuperable C1009

límite del compilador: las macros están demasiado anidadas

El compilador ha intentado expandir demasiadas macros al mismo tiempo. El compilador tiene un límite de 256 niveles de macros anidadas. Divida las macros anidadas en macros más sencillas.