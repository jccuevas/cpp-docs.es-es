---
title: Error del compilador C2218 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2218
dev_langs: C++
helpviewer_keywords: C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cce36d9e8d4e8f2ac82ddec9a967ac7e045b4a03
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2218"></a>Error del compilador C2218
'__vectorcall' no se puede usar con '/arch:IA32'  
  
 La convención de llamada `__vectorcall` solo se admite en código nativo en procesadores x86 y x64 que incluyen Extensiones SIMD de streaming 2 (SSE2) y versiones posteriores. Para obtener más información, consulte [__vectorcall](../../cpp/vectorcall.md).  
  
 Para corregir este error, cambie las opciones del compilador para que se dirijan a los conjuntos de instrucciones SSE2, AVX o AVX2. Para obtener más información, consulte [/arch (x86)](../../build/reference/arch-x86.md).