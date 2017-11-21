---
title: Compilador advertencia (nivel 1) C4729 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4729
dev_langs: C++
helpviewer_keywords: C4729
ms.assetid: 36a0151f-f258-48d9-9444-ae6d41ff70a4
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2d80512dd6aaecfbe1de06f69303eb3d42213856
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4729"></a>Advertencia del compilador (nivel 1) C4729
función demasiado grande para advertencias basadas en gráficos de flujos  
  
 Esta advertencia se genera cuando una función es demasiado grande para compilarse con una comprobación confiable en situaciones que generarían una advertencia. Esta advertencia solo se genera cuando se utiliza la opción del compilador [/Od](../../build/reference/od-disable-debug.md) .  
  
 Para resolver esta advertencia, divida la función en funciones más pequeñas.