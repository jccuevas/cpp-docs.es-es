---
title: Error del compilador C3293 | Documentos de Microsoft
ms.custom: 
ms.date: 07/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3293
dev_langs: C++
helpviewer_keywords: C3293
ms.assetid: b772cf98-52e0-4e24-be23-1f5d87d999ac
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ccf6bd08b1ca540fcdf46d18631e0ab11c7fe4f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3293"></a>Error del compilador C3293
'accessor': use 'default' para acceder a la propiedad predeterminada (indexador) de la clase 'type'  
  
 Se accedió incorrectamente a una propiedad indexada.  Vea [Cómo: utilizar propiedades en C++ / CLI](../../dotnet/how-to-use-properties-in-cpp-cli.md) para obtener más información.  

 **Visual Studio 2017 y versiones posterior**: en Visual Studio 2015 y versiones anterior, el compilador en algunos casos, pueden identificarse incorrectamente una propiedad predeterminada como un indizador predeterminado. Era posible solucionar el problema con el identificador "default" para acceder a la propiedad. La solución en sí misma se volvió problemática después de que se empezara a usar default como palabra clave en C++11. Por lo tanto, en Visual Studio 2017 se corrigieron los errores necesarios para la solución, y el compilador ahora genera un error cuando se usa "default" para acceder a la propiedad predeterminada de una clase.
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C3293 en Visual Studio 2015 y versiones anteriores.  
  
```  
// C3293.cpp  
// compile with: /clr /c  
using namespace System;  
ref class IndexerClass {  
public:  
   // default indexer  
   property int default[int] {  
      int get(int index) { return 0; }  
      void set(int index, int value) {}  
   }  
};  
  
int main() {  
   IndexerClass ^ ic = gcnew IndexerClass;  
   ic->Item[0] = 21;   // C3293 in VS2015 OK in VS2017
   ic->default[0] = 21;   // OK in VS2015 and earlier
  
   String ^s = "Hello";  
   wchar_t wc = s->Chars[0];   // C3293 in VS2015 OK in VS2017
   wchar_t wc2 = s->default[0];   // OK in VS2015 and earlier  
   Console::WriteLine(wc2);  
}  
```