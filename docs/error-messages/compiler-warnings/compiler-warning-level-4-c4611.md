---
title: Compilador advertencia (nivel 4) C4611 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4611
dev_langs: C++
helpviewer_keywords: C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3020cf7d115b735141b81e9007ac7fd027ed8674
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4611"></a>Advertencia del compilador (nivel 4) C4611
interacción entre 'función' y la destrucción de objetos de C++ es no portable  
  
 En algunas plataformas, las funciones que incluyen **catch** pueden no admitir la semántica de destrucción cuando se encuentra fuera del ámbito de objeto de C++.  
  
 Para evitar un comportamiento inesperado, evite el uso de **catch** en funciones que tienen constructores y destructores.  
  
 Esta advertencia solo se emite una vez; vea [advertencia pragma](../../preprocessor/warning.md).