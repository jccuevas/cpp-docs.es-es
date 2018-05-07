---
title: Compilador advertencia (nivel 4) C4611 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4611
dev_langs:
- C++
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5946c10b5e0e0e7e08f1ee37c77120896937adb1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4611"></a>Advertencia del compilador (nivel 4) C4611
interacción entre 'función' y la destrucción de objetos de C++ es no portable  
  
 En algunas plataformas, las funciones que incluyen **catch** pueden no admitir la semántica de destrucción cuando se encuentra fuera del ámbito de objeto de C++.  
  
 Para evitar un comportamiento inesperado, evite el uso de **catch** en funciones que tienen constructores y destructores.  
  
 Esta advertencia solo se emite una vez; vea [advertencia pragma](../../preprocessor/warning.md).