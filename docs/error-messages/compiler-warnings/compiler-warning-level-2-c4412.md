---
title: Compilador advertencia (nivel 2) C4412 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4412
dev_langs:
- C++
helpviewer_keywords:
- C4412
ms.assetid: f28dc531-1a98-497b-a366-0a13e1bc81c7
caps.latest.revision: 9
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
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 92aa12514088d0fbffbe826a495d76b49ab311d1
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-2-c4412"></a>Advertencia del compilador (nivel 2) C4412
'función': firma de la función contiene el tipo 'tipo'; Objetos de C++ son seguro pasar entre código puro y mixto o nativo.  
  
 El **/CLR: pure** opción del compilador está desusada en Visual Studio 2015.  
  
 El compilador detectó una situación potencialmente no segura que podría producir un error en tiempo de ejecución: se está realizando una llamada desde una **/CLR: pure** compilando una función que se importó mediante dllimport y la firma de función contiene un tipo no seguro. Un tipo no es seguro si contiene una función miembro o si tiene un miembro de datos es un tipo no seguro o un direccionamiento indirecto a un tipo no seguro.  
  
 Esto no es seguro debido a la diferencia en el valor predeterminado llamando a convenciones entre código puro y nativo (o mixto nativo y administrado). Al importar (a través de `dllimport`) una función en una **/CLR: pure** proceso de compilación, asegúrese de que las declaraciones de cada tipo en la firma son idénticas a las de la operación de compilación que exporta la función (con especial atención en las diferencias en las convenciones de llamada implícitas).  
  
 Una función miembro virtual es especialmente propensa a proporcionar resultados inesperados.  Sin embargo, incluso una función no virtual debe probarse para asegurarse de que obtiene los resultados correctos. Si está seguro de que está obteniendo los resultados correctos, puede omitir esta advertencia.  
  
 Para obtener más información sobre **/CLR: puro**, consulte [Cómo: migrar a/CLR: pure (C++ / CLI)](../../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md).  
  
 C4412 está desactivada de forma predeterminada. Consulte [advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) y [dllexport, dllimport](../../cpp/dllexport-dllimport.md) para obtener más información.  
  
 Para resolver esta advertencia, quite todas las funciones del tipo.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4412.  
  
```  
// C4412.cpp  
// compile with: /c /W2 /clr:pure  
#pragma warning (default : 4412)  
  
struct Unsafe {  
   virtual void __cdecl Test();  
};  
  
struct Safe {  
   int i;  
};  
  
__declspec(dllimport) Unsafe * __cdecl func();  
__declspec(dllimport) Safe * __cdecl func2();  
  
int main() {  
   Unsafe *pUnsafe = func();   // C4412  
   // pUnsafe->Test();  
  
   Safe *pSafe = func2();   // OK  
}  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente es un archivo de encabezado que declara dos tipos. El `Unsafe` tipo no es seguro porque tiene una función miembro.  
  
```  
// C4412.h  
struct Unsafe {  
   // will be __clrcall if #included in pure compilation  
   // defaults to __cdecl in native or mixed mode compilation  
   virtual void Test(int * pi);  
  
   // try the following line instead  
   // virtual void __cdecl Test(int * pi);  
};  
  
struct Safe {  
   int i;  
};  
```  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo exporta funciones con los tipos definidos en el archivo de encabezado.  
  
```  
// C4412_2.cpp  
// compile with: /LD  
#include "C4412.h"  
  
void Unsafe::Test(int * pi) {  
   *pi++;  
}  
  
__declspec(dllexport) Unsafe * __cdecl func() { return new Unsafe; }  
__declspec(dllexport) Safe * __cdecl func2() { return new Safe; }  
```  
  
## <a name="example"></a>Ejemplo  
 El valor predeterminado la convención de llamada un **/CLR: pure** compilación es diferente de una compilación nativa.  Cuando se incluye, C4412.h `Test` predeterminado es `__clrcall`. Si compila y ejecuta este programa (no utilice **/c**), el programa iniciará una excepción.  
  
 El ejemplo siguiente genera C4412.  
  
```  
// C4412_3.cpp  
// compile with: /W2 /clr:pure /c /link C4412_2.lib  
#pragma warning (default : 4412)  
#include "C4412.h"  
  
__declspec(dllimport) Unsafe * __cdecl func();  
__declspec(dllimport) Safe * __cdecl func2();  
  
int main() {  
   int n = 7;  
   Unsafe *pUnsafe = func();   // C4412  
   pUnsafe->Test(&n);  
  
   Safe *pSafe = func2();   // OK  
}  
```
