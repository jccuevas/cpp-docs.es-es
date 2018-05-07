---
title: Error irrecuperable C1013 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1013
dev_langs:
- C++
helpviewer_keywords:
- C1013
ms.assetid: 5514a679-efe7-4055-bdd3-5693ca0c332f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 00b5dae643ec20e9d7d8a8dcdf41d9debe7e6b7e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1013"></a>Error irrecuperable C1013
límite del compilador : hay demasiados paréntesis abiertos  
  
 Una expresión contiene demasiados niveles de paréntesis en una única expresión. Simplifique la expresión o divídala en varias instrucciones.  
  
 Antes de Visual C++ 6.0 Service Pack 3, el límite de paréntesis anidados en una única expresión era 59. Actualmente, el límite de paréntesis anidados es 256.