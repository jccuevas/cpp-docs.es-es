---
title: Error de compilador un error C2092 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2092
dev_langs:
- C++
helpviewer_keywords:
- C2092
ms.assetid: 037e44ae-16c8-489a-a512-dcdf7f7795a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 22b33680258358648737a9ae235c6f45f3592992
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2092"></a>Error de C2092 de Error de compilador
tipo de elemento de matriz 'nombre de la matriz' no puede ser una función  
  
 No se permiten matrices de funciones. Usar una matriz de punteros a funciones.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera un error C2092:  
  
```  
// C2092.cpp  
typedef void (F) ();  
typedef F AT[10];   // C2092  
```  
  
## <a name="example"></a>Ejemplo  
 Posible resolución:  
  
```  
// C2092b.cpp  
// compile with: /c  
typedef void (F) ();  
typedef F * AT[10];  
```