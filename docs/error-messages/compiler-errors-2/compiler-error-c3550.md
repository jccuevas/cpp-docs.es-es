---
title: Error del compilador C3550 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3550
dev_langs:
- C++
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91003af2069ba32083caefa8f5a79cbe0e7cd9c9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252899"
---
# <a name="compiler-error-c3550"></a>Error del compilador C3550
solo se permite 'decltype(auto)' sin formato en este contexto  
  
 Si se usa `decltype(auto)` como marcador de posición para el tipo de valor devuelto de una función, debe usarse por sí mismo. No se puede usar como parte de una declaración de puntero (`decltype(auto*)`), una declaración de referencia (`decltype(auto&)`) o cualquier otra cualificación similar.  
  
## <a name="see-also"></a>Vea también  
 [auto](../../cpp/auto-cpp.md)