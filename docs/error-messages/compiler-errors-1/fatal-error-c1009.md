---
title: Error irrecuperable C1009 | Documentos de Microsoft
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
ms.openlocfilehash: 665d868aeacbaf5c62bf59a4400baa2b31569972
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1009"></a>Error irrecuperable C1009
límite del compilador: las macros están demasiado anidadas  
  
 El compilador ha intentado expandir demasiadas macros al mismo tiempo. El compilador tiene un límite de 256 niveles de macros anidadas. Divida las macros anidadas en macros más sencillas.