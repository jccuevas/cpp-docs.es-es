---
title: "Error del compilador C2065 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2065"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2065"
ms.assetid: 78093376-acb7-45f5-9323-5ed7e0aab1dc
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# Error del compilador C2065
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador': identificador no declarado  
  
 El tipo de una variable se debe especificar en una declaración antes de poder usarla.  Los parámetros que usa una función se deben especificar en una declaración \(o prototipo\) para poder usar la función.  
  
 Causas posibles:  
  
1.  El nombre del identificador está mal escrito.  
  
2.  El identificador usa las letras mayúsculas y minúsculas incorrectas.  
  
3.  Faltan las comillas de cierre después de una constante de cadena.  
  
4.  Está efectuando la compilación con una versión de depuración del tiempo de ejecución de C, declarando una variable de iterador de la biblioteca estándar de C\+\+ en un bucle `for` e intentando usar esa variable fuera del ámbito del bucle `for`.  El hecho de compilar el código de la biblioteca estándar de C\+\+ con una versión de depuración del tiempo de ejecución de C implica [\/Zc:forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md).  Vea [Compatibilidad de los iteradores de depuración](../../standard-library/debug-iterator-support.md) para más información.  
  
5.  Es posible que esté llamando a una función en un archivo de encabezado SDK que actualmente no se admite en el entorno de compilación.  
  
6.  Está omitiendo archivos de inclusión necesarios, sobre todo si define `VC_EXTRALEAN`, `WIN32_LEAN_AND_MEAN` o `WIN32_EXTRA_LEAN`.  Estos símbolos excluyen algunos archivos de encabezado de windows.h y afxv\_w32.h para acelerar las compilaciones  \(busque en windows.h y afxv\_w32.h una descripción actualizada de lo que se excluye\).  
  
7.  Ámbito de espacio de nombres incorrecto.  Por ejemplo, para resolver funciones y operadores no completos de la biblioteca estándar de C\+\+, debe especificar el espacio de nombres `std` con la directiva `using`.  En el ejemplo siguiente se produce un error de compilación porque la directiva `using` no se ha convertido en comentario y se ha definido `cout` en el espacio de nombres `std`:  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2065 y muestra cómo corregirlo.  
  
```  
// C2065.cpp  
// compile with: /EHsc  
// using namespace std;   // Uncomment this line to fix  
#include <iostream>  
int main() {  
   cout << "Hello" << endl;   // C2065  
  
   // Or try the following line instead  
   std::cout << "Hello" << std::endl;  
}  
```  
  
## Ejemplo  
 Al llamar a una función genérica, si no se puede deducir el argumento de tipo previsto desde los parámetros usados, el compilador notificará un error.  Para más información, vea [Funciones genéricas \(C\+\+\/CLI\)](../../windows/generic-functions-cpp-cli.md).  
  
 El ejemplo siguiente genera el error C2065 y muestra cómo corregirlo.  
  
```  
// C2065_b.cpp  
// compile with: /clr  
generic <typename ItemType>  
void G(int i) {}  
  
int main() {  
   // global generic function call  
   G<T>(10);   // C2065  
   G<int>(10);   // OK - fix with a specific type argument  
}  
```  
  
## Ejemplo  
 Este error también puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual C\+\+ 2005: comprobación de parámetros de atributos de Visual C\+\+.  
  
 El ejemplo siguiente genera el error C2065 y muestra cómo corregirlo.  
  
```  
// C2065_c.cpp  
// compile with: /c  
[module(DLL, name=MyLibrary)];   // C2065  
// try the following line instead  
// [module(dll, name="MyLibrary")];  
  
[export]  
struct MyStruct {  
   int i;  
};  
```