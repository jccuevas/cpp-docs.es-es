---
title: Error irrecuperable C1009 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1009
dev_langs:
- C++
helpviewer_keywords:
- C1009
ms.assetid: dcc8383c-3362-4c47-9c26-25d2451ebd53
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b1fbd8994be6fd86a764db400d8761a5d697079b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037338"
---
# <a name="fatal-error-c1009"></a>Error irrecuperable C1009

límite del compilador: las macros están demasiado anidadas

El compilador ha intentado expandir demasiadas macros al mismo tiempo. El compilador tiene un límite de 256 niveles de macros anidadas. Divida las macros anidadas en macros más sencillas.