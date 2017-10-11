---
title: Error del compilador C3550 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3550
dev_langs:
- C++
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 52b3e3323bac9ad55ff10481b3504e4e054ba874
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3550"></a>Error del compilador C3550
solo se permite 'decltype(auto)' sin formato en este contexto  
  
 Si se usa `decltype(auto)` como marcador de posición para el tipo de valor devuelto de una función, debe usarse por sí mismo. No se puede usar como parte de una declaración de puntero (`decltype(auto*)`), una declaración de referencia (`decltype(auto&)`) o cualquier otra cualificación similar.  
  
## <a name="see-also"></a>Vea también  
 [auto](../../cpp/auto-cpp.md)
