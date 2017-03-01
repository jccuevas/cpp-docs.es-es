---
title: Compilador advertencia (nivel 1) C4342 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4342
dev_langs:
- C++
helpviewer_keywords:
- C4342
ms.assetid: 47d4d5ab-069f-4cdc-98c3-10d649577a37
caps.latest.revision: 10
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
ms.openlocfilehash: 4755edcc99a9b8fca00972611bbd633a68eb8ec7
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4342"></a>Advertencia del compilador (nivel 1) C4342
cambio en el comportamiento: se llamó a 'función', pero en versiones anteriores se llamaba a un operador de miembro  
  
 En versiones anteriores de Visual C++, se llama a un miembro, pero este comportamiento se ha modificado y el compilador busca a la mejor coincidencia en el ámbito de espacio de nombres.  
  
 Si se encontró un operador de miembro, el compilador no consideraría previamente ningún espacio de nombres operadores de ámbito. Si hay una coincidencia mejor en el ámbito de espacio de nombres, el compilador actual lo llamará correctamente, mientras que los compiladores anteriores no lo considerarían.  
  
 Esta advertencia se debería deshabilitar después trasladado correctamente el código a la versión actual.  El compilador puede proporcionar falsos positivos, generando esta advertencia para código donde no hay ningún cambio de comportamiento.  
  
 De forma predeterminada, esta advertencia está desactivada. Para obtener más información, consulte [advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 El ejemplo siguiente genera C4342:  
  
```  
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
