---
title: Error del compilador C2929 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2929
dev_langs:
- C++
helpviewer_keywords:
- C2929
ms.assetid: 11134027-6adc-4733-b6bd-b94486bd1933
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7a6069060541f884bfbeb298845f5001b35d561
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33244965"
---
# <a name="compiler-error-c2929"></a>Error del compilador C2929
'identifier': creación de instancias explícita; no se puede forzar y suprimir de forma explícita la creación de instancias de miembros de clase de plantilla  
  
 No se puede usar con instancias explícitamente un identificador mientras se evita que este se use con instancias.  
  
 El ejemplo siguiente genera la advertencia C2929:  
  
```  
// C2929.cpp  
// compile with: /c  
template<typename T>  
class A {  
public:  
   A() {}  
};  
  
template A<int>::A();  
  
extern template A<int>::A();   // C2929  
```