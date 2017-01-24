---
title: "/Zc:rvalueCast (Exigir reglas de conversi&#243;n de tipos) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "rvaluecast"
  - "/Zc:rvalueCast"
  - "VC.Project.VCCLCompilerTool.EnforceTypeConversionRules"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zc (opción del compilador) (C++)"
  - "Exigir reglas de conversión de tipos"
  - "rvaluecast"
  - "Zc (opción del compilador) (C++)"
  - "-Zc (opción del compilador) (C++)"
ms.assetid: 7825277d-e565-4c48-b0fb-76ac0b0c6e38
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Zc:rvalueCast (Exigir reglas de conversi&#243;n de tipos)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cuando se especifica la opción **\/Zc:rvalueCast**, el compilador identifica correctamente un tipo de referencia de valor R como resultado de una operación de conversión de acuerdo con el estándar C\+\+11.  Cuando no se especifica la opción, el comportamiento del compilador es el mismo que en Visual Studio 2012.  La opción **\/Zc:rvalueCast** está desactivada de manera predeterminada.  Por conformidad y para eliminar los errores en el uso de las conversiones, recomendamos utilizar **\/Zc:rvalueCast**.  
  
## Sintaxis  
  
```  
/Zc:rvalueCast[-]  
```  
  
## Comentarios  
 Si se especifica **\/Zc:rvalueCast**, el compilador sigue la sección 5.4 del estándar C\+\+11 y trata únicamente las expresiones de conversión que tienen como resultado tipos sin referencia y las que tienen como resultado referencias de valor R a tipos que no son de función como, por ejemplo, los tipos de valor R.  De forma predeterminada o si se especifica **\/Zc:rvalueCast\-**, el compilador no es conforme y trata como valores R todas las expresiones de conversión que tienen como resultado referencias de valor R.  
  
 Use **\/Zc:rvalueCast** si pasa una expresión de conversión como argumento a una función que toma un tipo de referencia de valor R.  El comportamiento predeterminado genera el error del compilador [C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) cuando el compilador determina incorrectamente el tipo de la expresión de conversión.  Este ejemplo muestra un error del compilador en código correcto cuando no se especifica \/Zc:rvalueCast:  
  
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
  
 Puede que el comportamiento predeterminado del compilador no notifique el error C2102 cuando proceda.  En este ejemplo, el compilador no notifica un error si se toma la dirección de un valor R creado por una conversión de identidad cuando no se especifica **\/Zc:rvalueCast**:  
  
```cpp  
int main() {  
   int a = 1;  
   int *p = &a;   // Okay, take address of lvalue   
                  // Identity cast creates rvalue from lvalue;    
   p = &(int)a;   // problem: should cause C2102: '&' requires l-value  
}  
```  
  
 Para obtener más información sobre los problemas de conformidad en Visual C\+\+, vea [Comportamiento no estándar](../../cpp/nonstandard-behavior.md).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione la carpeta **C\/C\+\+**.  
  
3.  Seleccione la página de propiedades **Línea de comandos**.  
  
4.  Modifique la propiedad **Opciones adicionales** para incluir **\/Zc:rvalueCast** y, a continuación, elija **Aceptar**.  
  
## Vea también  
 [\/Zc \(Ajuste\)](../../build/reference/zc-conformance.md)