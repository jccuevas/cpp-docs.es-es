---
title: Error del compilador C2936 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2936
dev_langs:
- C++
helpviewer_keywords:
- C2936
ms.assetid: 5d1ba0fc-0c78-4a37-a83b-1ef8527763be
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3d3cfd6e9142e5c10906eaa94d5a1466b0d0bd19
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2936"></a>Error del compilador C2936
'clase': el id. de clase de plantilla se ha vuelto a definir como variable de datos global  
  
 No se puede usar una clase genérica o de plantilla como variable de datos local.  
  
 Este error puede generarse si las llaves no tienen su pareja correspondiente.  
  
 El ejemplo siguiente genera la advertencia C2936:  
  
```  
// C2936.cpp  
// compile with: /c  
template<class T> struct TC { };   
int TC<int>;   // C2936  
  
// OK  
struct TC2 { };   
int TC2;  
```  
  
 También se puede producir el error C2936 al usar genéricos:  
  
```  
// C2936b.cpp  
// compile with: /clr /c  
generic<class T>  
ref struct GC {};  
int GC<int>;   // C2936  
  
// OK  
ref struct GC2 {};  
int GC2;  
```