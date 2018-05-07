---
title: Error del compilador C3293 | Documentos de Microsoft
ms.custom: ''
ms.date: 07/21/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3293
dev_langs:
- C++
helpviewer_keywords:
- C3293
ms.assetid: b772cf98-52e0-4e24-be23-1f5d87d999ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b195a91825b0f20445b29e330f67810329584db7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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