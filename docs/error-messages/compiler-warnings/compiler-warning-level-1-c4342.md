---
title: Compilador advertencia (nivel 1) C4342 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4342
dev_langs:
- C++
helpviewer_keywords:
- C4342
ms.assetid: 47d4d5ab-069f-4cdc-98c3-10d649577a37
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7d2a3550a3d1b7333412b7828809120db89c60b2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4342"></a>Advertencia del compilador (nivel 1) C4342
cambio de comportamiento: '*función*' llama, pero en versiones anteriores se llamaba a un operador de miembro  
  
 En versiones de Visual C++ antes de Visual Studio 2002, se llama a un miembro, pero este comportamiento se ha cambiado y ahora el compilador busca a la mejor coincidencia en el ámbito de espacio de nombres.  
  
 Si se encontró un operador de miembro, el compilador no consideraría previamente ningún espacio de nombres operadores de ámbito. Si hay una coincidencia mejor en el ámbito de espacio de nombres, el compilador actual llama correctamente a él, mientras que los compiladores anteriores no lo considerarían.  
  
 Esta advertencia se debe deshabilitar después correctamente trasladar el código a la versión actual.  El compilador puede proporcionar falsos positivos, generando esta advertencia para el código que no haya ningún cambio de comportamiento.  
  
 De forma predeterminada, esta advertencia está desactivada. Para obtener más información, consulte [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 El ejemplo siguiente genera C4342:  
  
```cpp  
// C4342.cpp  
// compile with: /EHsc /W1  
#include <fstream>  
#pragma warning(default: 4342)  
using namespace std;  
struct X : public ofstream {  
   X();  
};  
  
X::X() {  
   open( "ofs_bug_ev.txt." );  
   if ( is_open() ) {  
      *this << "Text" << "<-should be text" << endl;   // C4342  
      *this << ' ' << "<-should be space symbol" << endl;   // C4342  
   }  
}  
  
int main() {  
   X b;  
   b << "Text" << "<-should be text" << endl;  
   b << ' ' << "<-should be space symbol" << endl;  
}  
```