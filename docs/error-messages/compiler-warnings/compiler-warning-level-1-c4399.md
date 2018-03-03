---
title: Compilador advertencia (nivel 1) C4399 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4399
dev_langs:
- C++
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eff01c29d423b0823b41bf63702cf42ee839a523
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4399"></a>Advertencia del compilador (nivel 1) C4399
'símbolo': símbolo de por proceso no se debe marcar con __declspec (dllimport) cuando se compila con/CLR: pure  
  
 El **/CLR: pure** opción del compilador está en desuso en Visual Studio 2015.  
  
 No se pueden importar datos de una imagen nativa o una imagen con construcciones nativas y CLR en una imagen pura. Para resolver esta advertencia, compile con **/CLR** (no **/CLR: pure**) o eliminar `__declspec(dllimport)`.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4399.  
  
```  
// C4399.cpp  
// compile with: /clr:pure /doc /W1 /c  
__declspec(dllimport) __declspec(process) extern const int i;   // C4399  
```