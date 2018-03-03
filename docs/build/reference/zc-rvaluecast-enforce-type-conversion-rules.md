---
title: "-Zc: rvalueCast (exigir reglas de conversión de tipos) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- rvaluecast
- /Zc:rvalueCast
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- rvaluecast
- Enforce type conversion rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 7825277d-e565-4c48-b0fb-76ac0b0c6e38
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f4b888dde70708ee10b2d8000ff6380709dc870
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="zcrvaluecast-enforce-type-conversion-rules"></a>/Zc:rvalueCast (Exigir reglas de conversión de tipos)
Cuando el **/Zc: rvaluecast** se especifica la opción, el compilador identifica correctamente un tipo de referencia de valor r como resultado de una operación de conversión de acuerdo con el estándar C ++ 11. Cuando no se especifica la opción, el comportamiento del compilador es el mismo que en Visual Studio 2012. De forma predeterminada, **/Zc: rvaluecast** está desactivada. Por conformidad y para eliminar los errores en el uso de conversiones, recomendamos que use **/Zc: rvaluecast**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Zc:rvalueCast[-]  
```  
  
## <a name="remarks"></a>Comentarios  
 Si **/Zc: rvaluecast** se especifica, el compilador sigue la sección 5.4 del estándar C ++ 11 y trata sólo convertir expresiones que producen tipos sin referencia y conversión expresiones que producen las referencias de valor r a tipos de función no como tipos de valor r. De forma predeterminada, o si **/Zc:rvalueCast-** se especifica, el compilador no es conforme y trata todas las expresiones de conversión que dan como resultado referencias a valor r como valores r.  
  
 Use **/Zc: rvaluecast** si se pasa una expresión de conversión como argumento a una función que toma un tipo de referencia rvalue. El comportamiento predeterminado genera el error del compilador [el error C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) cuando el compilador determina incorrectamente el tipo de la expresión de conversión. Este ejemplo muestra un error del compilador en código correcto cuando no se especifica /Zc:rvalueCast:  
  
```cpp  
// Test of /Zc:rvalueCast  
// compile by using:  
// cl /c /Zc:rvalueCast- make_thing.cpp  
// cl /c /Zc:rvalueCast make_thing.cpp  
  
#include <utility>  
  
template <typename T>   
struct Thing {  
   // Construct a Thing by using two rvalue reference parameters  
   Thing(T&& t1, T&& t2)  
      : thing1(t1), thing2(t2) {}  
  
   T& thing1;  
   T& thing2;  
};  
  
// Create a Thing, using move semantics if possible  
template <typename T>  
Thing<T> make_thing(T&& t1, T&& t2)  
{  
   return (Thing<T>(std::forward<T>(t1), std::forward<T>(t2)));  
}  
  
struct Test1 {  
   long a;  
   long b;  
  
   Thing<long> test() {   
      // Use identity casts to create rvalues as arguments  
      return make_thing(static_cast<long>(a), static_cast<long>(b));   
   }  
};  
  
```  
  
 Puede que el comportamiento predeterminado del compilador no notifique el error C2102 cuando proceda. En este ejemplo, el compilador no notifica un error si se toma la dirección de un valor r creado por una conversión de identidad cuando **/Zc: rvaluecast** no se especifica:  
  
```cpp  
int main() {  
   int a = 1;  
   int *p = &a;   // Okay, take address of lvalue   
                  // Identity cast creates rvalue from lvalue;    
   p = &(int)a;   // problem: should cause C2102: '&' requires l-value  
}  
```  
  
 Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **C/C++** carpeta.  
  
3.  Seleccione el **línea de comandos** página de propiedades.  
  
4.  Modificar el **opciones adicionales** propiedad para incluir **/Zc: rvaluecast** y, a continuación, elija **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [/Zc (ajuste)](../../build/reference/zc-conformance.md)