---
title: Compilador advertencia (nivel 4) C4431 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4431
dev_langs:
- C++
helpviewer_keywords:
- C4431
ms.assetid: 58434ab6-dd8d-427b-953a-602fb7453ae6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6594d50cf3688565bc2570ba536ddb908c482f23
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4431"></a>Advertencia del compilador (nivel 4) C4431
falta el especificador de tipo; se presupone int. Nota: C no admite default-int  
  
 Este error puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual C++ 2005: Visual C++ ya no crea identificadores sin tipo como int de forma predeterminada. El tipo de un identificador debe especificarse explícitamente.  
  
 De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4431.  
  
```  
// C4431.c  
// compile with: /c /W4  
#pragma warning(default:4431)  
i;   // C4431  
int i;   // OK  
```