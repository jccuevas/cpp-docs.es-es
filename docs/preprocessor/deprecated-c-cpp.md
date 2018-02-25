---
title: en desuso) (C/C ++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc-pragma.deprecated
- deprecated_CPP
dev_langs:
- C++
helpviewer_keywords:
- deprecated pragma
- pragmas, deprecated
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a5df80fffb5b9cdeabfe19d5a5de6eb771d35d3d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="deprecated-cc"></a>(C/C++) en desuso
El **en desuso** permite de pragma que indique que un tipo de función o cualquier otro identificador puede ya no admitirse en una futura versión o ya no debe usarse.  
> [!NOTE]
> Para obtener información sobre C ++ 14 `[[deprecated]]` atributo y orientación sobre cuándo usar este atributo vs el modificador declspec de Microsoft o la directiva pragma, consulte [atributos estándar de C++](../cpp/attributes2.md) atributo.
  
## <a name="syntax"></a>Sintaxis  
  
```  
#pragma deprecated( identifier1 [,identifier2, ...] )  
```  
  
## <a name="remarks"></a>Comentarios  
 Cuando el compilador encuentra un identificador especificado por un **en desuso** pragma, que emite la advertencia del compilador [C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md).   
  
 Puede desusar nombres de macro. Coloque el nombre de la macro entre comillas; de lo contrario se producirá la expansión de la macro.  
  
 Dado que la **en desuso** pragma funciona en todos los identificadores coincidentes y no tiene en cuenta las firmas, no es la mejor opción para dejar en desuso versiones específicas de funciones sobrecargadas. Cualquier nombre de la función de búsqueda de coincidencias se incluyen en el ámbito, genera la advertencia.

  Se recomienda usar C ++ 14 `[[deprecated]]` atributo, siempre que sea posible, en lugar de la **en desuso** pragma. Específico de Microsoft [__declspec (deprecated)](../cpp/deprecated-cpp.md) modificador de declaración también es una opción mejor en muchos casos que el **en desuso** pragma. El `[[deprecated]]` atributo y `__declspec(deprecated)` modificador le permiten especificar el estado desusado para formas concretas de funciones sobrecargadas. La advertencia diagnóstico sólo aparece en las referencias a la función sobrecargada concreta el atributo o modificador que se aplica a.  
  
## <a name="example"></a>Ejemplo  
  
```  
// pragma_directive_deprecated.cpp  
// compile with: /W3  
#include <stdio.h>  
void func1(void) {  
}  
  
void func2(void) {  
}  
  
int main() {  
   func1();  
   func2();  
   #pragma deprecated(func1, func2)  
   func1();   // C4995  
   func2();   // C4995  
}  
```  
  
 En el ejemplo siguiente se muestra cómo desusar una clase:  
  
```  
// pragma_directive_deprecated2.cpp  
// compile with: /W3  
#pragma deprecated(X)  
class X {  // C4995  
public:  
   void f(){}  
};  
  
int main() {  
   X x;   // C4995  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)