---
title: Error del compilador C2435 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2435
dev_langs:
- C++
helpviewer_keywords:
- C2435
ms.assetid: be6aa8f8-579b-42ea-bdd8-2d01393646ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 44c4dec71cdf077dc8fbd1ba81b555090b524007
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2435"></a>Error del compilador C2435
'var': la inicialización dinámica requiere CRT administrado, no se puede compilar con/CLR: safe  
  
 Las opciones del compilador **/clr:pure** y **/clr:safe** están en desuso en Visual Studio 2015.  
  
 Inicialización de variable global de dominio por aplicación requiere compilada CRT con `/clr:pure`, que no genera una imagen comprobable.  
  
 Para obtener más información, consulte [appdomain](../../cpp/appdomain.md) y [process](../../cpp/process.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C2435:  
  
```  
// C2435.cpp  
// compile with: /clr:safe /c  
int globalvar = 0;   // C2435  
  
__declspec(process)  
int globalvar2 = 0;  
```