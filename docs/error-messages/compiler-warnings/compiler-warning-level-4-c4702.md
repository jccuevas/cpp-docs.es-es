---
title: Compilador advertencia (nivel 4) C4702 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4702
dev_langs:
- C++
helpviewer_keywords:
- C4702
ms.assetid: d8198c1e-8762-42a6-9e6b-cb568b7a1686
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9ef7420f3699363d33d195e2455ab9fddf88de40
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4702"></a>Advertencia del compilador (nivel 4) C4702
código inalcanzable  
  
 Esta advertencia es el resultado del trabajo de conformidad del compilador efectuado para Visual Studio .NET 2003: código inalcanzable. Cuando el compilador (back-end) detecte código inalcanzable, generará la advertencia C4702, una advertencia de nivel 4.  
  
 Para que el código sea válido en las versiones tanto el Visual Studio .NET 2003 y Visual Studio .NET de Visual C++, quite el código inalcanzable o asegúrese de que todo el código fuente es alcanzable por algún flujo de ejecución.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C4702.  
  
```  
// C4702.cpp  
// compile with: /W4  
#include <stdio.h>  
  
int main() {  
   return 1;  
   printf_s("I won't print.\n");   // C4702 unreachable  
}  
```  
  
## <a name="example"></a>Ejemplo  
 Cuando se compila con **/GX**, **/EHc**, **/EHsc**, o **/EHac** y las funciones extern C código puede ser inalcanzable porque extern C se supone que las funciones no throw, lo que el bloque catch no está accesible.  Si cree que esta advertencia no es válida debido a que una función puede producir, compile con **/EHa** o **/EHs**, en función de la excepción producida.  
  
 Para obtener más información, consulte [/EH (modelo de control de excepciones)](../../build/reference/eh-exception-handling-model.md) para obtener más información.  
  
 El ejemplo siguiente genera la advertencia C4702.  
  
```  
// C4702b.cpp  
// compile with: /W4 /EHsc  
#include <iostream>  
  
using namespace std;  
extern "C" __declspec(dllexport) void Function2(){}  
  
int main() {  
   try {  
      Function2();  
   }  
   catch (...) {  
      cout << "Exp: Function2!" << endl;   // C4702  
   }  
}  
```