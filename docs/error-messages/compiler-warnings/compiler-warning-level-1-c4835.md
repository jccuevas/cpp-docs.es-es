---
title: Compilador advertencia (nivel 1) C4835 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4835
dev_langs:
- C++
helpviewer_keywords:
- C4835
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 7eff3fd7ab97b978ccc9e146eabf500c7dbedf0f
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4835"></a>Advertencia del compilador (nivel 1) C4835
'variable': el inicializador de los datos exportados no se ejecutará hasta que el código administrado se ejecuta primero en el ensamblado de host  
  
 Al obtener acceso a datos entre componentes administrados, se recomienda no usar la importación de C++ nativo y mecanismos de exportación. En su lugar, declare los miembros de datos dentro de un tipo administrado y hacer referencia a los metadatos con `#using` en el cliente. Para obtener más información, consulte [# directiva using](../../preprocessor/hash-using-directive-cpp.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4835.  
  
```  
// C4835.cpp  
// compile with: /W1 /clr /LD  
int f() { return 1; }  
int n = 9;  
  
__declspec(dllexport) int m = f();   // C4835  
__declspec(dllexport) int *p = &n;   // C4835  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se utiliza el componente creado en el ejemplo anterior, que muestra que el valor de las variables no según lo esperado.  
  
```  
// C4835_b.cpp  
// compile with: /clr C4835.lib  
#include <stdio.h>  
__declspec(dllimport) int m;  
__declspec(dllimport) int *p;  
  
int main() {  
   printf("%d\n", m);  
   printf("%d\n", p);  
}  
```  
  
```Output  
0  
268456008  
```
