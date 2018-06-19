---
title: Error del compilador C2513 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2513
dev_langs:
- C++
helpviewer_keywords:
- C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 704e5d71301886d46c8a2ce08d7ea34ef1f8275a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33228263"
---
# <a name="compiler-error-c2513"></a>Error del compilador C2513
'type': no hay ninguna variable declarada antes de '='  
  
 El especificador de tipo aparece en la declaración con ningún identificador de variable.  
  
 El ejemplo siguiente genera C2513:  
  
```  
// C2513.cpp  
int main() {  
   int = 9;   // C2513  
   int i = 9;   // OK  
}  
```  
  
 Este error también puede generarse como resultado del trabajo de conformidad del compilador realizado para Visual Studio .NET 2003: inicialización de una definición de tipo ya no se permite. La inicialización de una definición de tipo no está permitida por el estándar y ahora genera un error del compilador.  
  
```  
// C2513b.cpp  
// compile with: /c  
typedef struct S {  
   int m_i;  
} S = { 1 };   // C2513  
// try the following line instead  
// } S;  
```  
  
 Una alternativa sería eliminar `typedef` definir una variable con la lista de inicializadores agregado, pero esto no se recomienda porque creará una variable con el mismo nombre que el tipo y ocultar el nombre de tipo.