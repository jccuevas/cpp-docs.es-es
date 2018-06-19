---
title: Compilador advertencia (nivel 3) C4723 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4723
dev_langs:
- C++
helpviewer_keywords:
- C4723
ms.assetid: 07669d14-3fd8-4a43-94bc-b61c50e58460
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c5f91bbdc60ab1901c4afe4d5bea9f3258692ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33296619"
---
# <a name="compiler-warning-level-3-c4723"></a>Advertencia del compilador (nivel 3) C4723
posible división por 0  
  
 El segundo operando en una operación de división que se evalúa como cero en tiempo de compilación, que da resultados no definidos.  
  
 Esta advertencia se emite cuando se usa [/Og](../../build/reference/og-global-optimizations.md) o una opción de optimización que implique/Og.  
  
 Puede que el compilador ha generado el operando cero.