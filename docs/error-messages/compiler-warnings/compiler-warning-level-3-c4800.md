---
title: Advertencia (nivel 3) del compilador C4800 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4800
dev_langs:
- C++
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 687b0dab996bfbfe2ce30d65b86196383c02b914
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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