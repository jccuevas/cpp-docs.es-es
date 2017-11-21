---
title: Compilador advertencia (nivel 1) C4182 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4182
dev_langs: C++
helpviewer_keywords: C4182
ms.assetid: 8970f3c6-e2dd-407e-b2ec-964360eb8b43
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dfd94e5c98e1ca6e19e3e34c3028c93148871cf4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4182"></a>Advertencia del compilador (nivel 1) C4182
\#incluir es el nivel de anidamiento 'número' profundas; posible recursividad infinita  
  
 El compilador se quedó sin espacio en el montón debido al número de archivos de inclusión anidados. Un archivo de inclusión está anidado cuando se incluye desde otro archivo de inclusión.  
  
 Este mensaje es informativo y precede al error [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md).