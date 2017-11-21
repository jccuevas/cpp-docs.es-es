---
title: Compilador advertencia (nivel 3) C4023 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4023
dev_langs: C++
helpviewer_keywords: C4023
ms.assetid: 615d5374-d7c1-42eb-acfd-917c053270c8
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 170a76381dac09ad0543b30e71aedb306b514379
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4023"></a>Advertencia del compilador (nivel 3) C4023
'símbolo': el puntero con base se pasó a la función sin prototipo: número de parámetro  
  
 Si se pasa un puntero con base a una función sin prototipo, el puntero se normaliza, con resultados imprevisibles.  
  
 Para resolver esta advertencia, use funciones prototipo a las que se pasan punteros con base.