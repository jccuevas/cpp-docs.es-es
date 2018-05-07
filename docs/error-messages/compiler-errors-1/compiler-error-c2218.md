---
title: Error del compilador C2218 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2218
dev_langs:
- C++
helpviewer_keywords:
- C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1efda7258616862efc464b493b51ada2c6bd7674
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2218"></a>Error del compilador C2218
'__vectorcall' no se puede usar con '/arch:IA32'  
  
 La convención de llamada `__vectorcall` solo se admite en código nativo en procesadores x86 y x64 que incluyen Extensiones SIMD de streaming 2 (SSE2) y versiones posteriores. Para obtener más información, consulte [__vectorcall](../../cpp/vectorcall.md).  
  
 Para corregir este error, cambie las opciones del compilador para que se dirijan a los conjuntos de instrucciones SSE2, AVX o AVX2. Para obtener más información, consulte [/arch (x86)](../../build/reference/arch-x86.md).