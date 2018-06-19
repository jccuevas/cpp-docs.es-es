---
title: Advertencia (nivel 3) del compilador C4800 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4800
dev_langs:
- C++
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed4b14ae2f3af3218909d6cd4609f1f45d3d7cc2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293639"
---
# <a name="compiler-warning-level-3-c4800"></a>Advertencia del compilador (nivel 3) C4800  
  
> '*tipo*': forzando el valor a bool 'true' o 'false' (advertencia de rendimiento)  
  
Esta advertencia se genera cuando un valor que no es `bool` se asignan o se convierten en tipo `bool`. Normalmente, este mensaje se producen mediante la asignación de `int` variables a `bool` variables donde la `int` variable contenga solamente valores **true** y **false**y podría ser volver a declarar como tipo `bool`. Si no se vuelve a escribir la expresión para utilizar el tipo `bool`, a continuación, puede agregar "`!=0`" a la expresión, que proporciona el tipo de expresión `bool`. Convertir la expresión al tipo `bool` no deshabilita la advertencia, que forma parte del diseño.  
  
Esta advertencia ya no se genera en Visual Studio de 2017.  
  
## <a name="example"></a>Ejemplo
  
 El ejemplo siguiente genera C4800 y muestra cómo corregirlo:  
  
```cpp  
// C4800.cpp  
// compile with: /W3  
int main() {  
   int i = 0;  
  
   // To fix, instead try:  
   // bool i = 0;  
  
   bool j = i;   // C4800  
   j++;  
}  
```