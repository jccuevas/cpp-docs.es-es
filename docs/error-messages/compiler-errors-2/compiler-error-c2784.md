---
title: Compilador Error C2784 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2784
dev_langs:
- C++
helpviewer_keywords:
- C2784
ms.assetid: 3d761fe2-881c-48bd-afae-e2e714e20473
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: beca5e3db426828eeec884cfc8e5e6048006fcd5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233323"
---
# <a name="compiler-error-c2784"></a>Compilador Error C2784
'declaration' : no se pudo deducir el argumento de plantilla para 'type' de 'type'  
  
 El compilador no puede determinar un argumento de plantilla a partir de los argumentos de función proporcionados.  
  
 El siguiente ejemplo genera el error C2784 e indica cómo corregirlo:  
  
```  
// C2784.cpp  
template<class T> class X {};  
template<class T> void f(X<T>) {}  
  
int main() {  
   X<int> x;  
   f(1);   // C2784  
  
   // To fix it, try the following line instead  
   f(x);  
}  
```