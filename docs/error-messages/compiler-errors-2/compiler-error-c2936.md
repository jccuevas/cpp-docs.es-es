---
title: Error del compilador C2936 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2936
dev_langs: C++
helpviewer_keywords: C2936
ms.assetid: 5d1ba0fc-0c78-4a37-a83b-1ef8527763be
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b6c8c8661d4f1c1ecaf80ed35ec2153616e03b87
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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