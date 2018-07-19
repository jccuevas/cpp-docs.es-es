---
title: C2665 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2665
dev_langs:
- C++
helpviewer_keywords:
- C2665
ms.assetid: a7f99b61-2eae-4f2b-ba75-ea68fd1e8312
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18cc99d6ea0a45e7c096a13cfe57dc841ca351bf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33235785"
---
# <a name="compiler-error-c2665"></a>C2665 de Error del compilador
'función': ninguna de las sobrecargas número1 puede convertir el parámetro número2 del tipo 'tipo'  
  
 Un parámetro de la función sobrecargada no se puede convertir al tipo requerido.  Soluciones posibles:  
  
-   Proporcione un operador de conversión.  
  
-   Utilice una conversión explícita.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C2665.  
  
```  
// C2665.cpp  
void func(short, char*){}  
void func(char*, char*){}  
  
int main() {  
   func(0, 1);   // C2665  
   func((short)0, (char*)1);   // OK  
}  
```