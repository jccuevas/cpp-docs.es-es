---
title: Error de compilador Error C2780 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2780
dev_langs:
- C++
helpviewer_keywords:
- C2780
ms.assetid: 423793d8-a3b2-4f35-85f8-ae1d043e2b69
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fba3d16284e8f56dd3583cb73d4b8fec56222a38
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33232730"
---
# <a name="compiler-error-c2780"></a>Error C2780 de Error del compilador
'declaration' : se esperan N argumentos; M proporcionado  
  
 Una plantilla de función tiene muchos o pocos argumentos.  
  
 El siguiente ejemplo genera el error C2780 y muestra cómo corregirlo:  
  
```  
// C2780.cpp  
template<typename T>  
void f(T, T){}  
  
int main() {  
   f(1);  // C2780  
   // try the following line instead  
   // f(1,2);  
}  
```