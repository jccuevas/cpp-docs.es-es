---
title: Error irrecuperable C1009 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1009
dev_langs:
- C++
helpviewer_keywords:
- C1009
ms.assetid: dcc8383c-3362-4c47-9c26-25d2451ebd53
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 68919abc1bc9ed498d7e9715396b501e9f6fb6b5
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1009"></a>Error irrecuperable C1009
límite del compilador: las macros están demasiado anidadas  
  
 El compilador ha intentado expandir demasiadas macros al mismo tiempo. El compilador tiene un límite de 256 niveles de macros anidadas. Divida las macros anidadas en macros más sencillas.
