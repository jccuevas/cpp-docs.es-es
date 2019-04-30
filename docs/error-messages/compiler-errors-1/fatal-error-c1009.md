---
title: Error irrecuperable C1009
ms.date: 11/04/2016
f1_keywords:
- C1009
helpviewer_keywords:
- C1009
ms.assetid: dcc8383c-3362-4c47-9c26-25d2451ebd53
ms.openlocfilehash: c4654d37f5ce184f6fa5b8888e6ca0184267be07
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62364316"
---
# <a name="fatal-error-c1009"></a>Error irrecuperable C1009

límite del compilador: las macros están demasiado anidadas

El compilador ha intentado expandir demasiadas macros al mismo tiempo. El compilador tiene un límite de 256 niveles de macros anidadas. Divida las macros anidadas en macros más sencillas.