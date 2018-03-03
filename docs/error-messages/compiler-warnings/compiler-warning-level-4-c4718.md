---
title: Compilador advertencia (nivel 4) C4718 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4718
dev_langs:
- C++
helpviewer_keywords:
- C4718
ms.assetid: 29507f8a-b024-42c1-a3b8-f35d1f2641f3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 214c481f4ad77a7a67190cd7427e0cd5775ccc8c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4718"></a>Advertencia del compilador (nivel 4) C4718
'llamada a función': la llamada recursiva no tiene efectos secundarios; se eliminará  
  
 Una función contiene una llamada recursiva, pero no tiene efectos secundarios. Se está eliminando una llamada a esta función. La precisión del programa no se ve afectada, pero sí el comportamiento. Dado que si se deja la llamada entrante podría producirse una excepción de desbordamiento de pila en tiempo de ejecución, la eliminación de la llamada evita esa posibilidad.