---
title: "Problemas en la inclusi&#243;n de funciones en l&#237;nea | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Ob1 (opción del compilador de C++)"
  - "/Ob2 (opción del compilador de C++)"
  - "problemas en la inclusión de funciones en línea"
  - "funciones inline, problemas"
  - "-Ob1 (opción del compilador) [C++]"
  - "-Ob2 (opción del compilador de C++)"
ms.assetid: 65d59943-4b3c-4a43-aeb6-dccbf7686740
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Problemas en la inclusi&#243;n de funciones en l&#237;nea
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Si se usa la inclusión de funciones en línea, es necesario:  
  
-   Implementar las funciones en línea en el archivo de encabezado incluido.  
  
-   Activar la inclusión de funciones en línea en el archivo de encabezado.  
  
```  
// LNK2019_function_inline.cpp  
// compile with: /c   
// post-build command: lib LNK2019_function_inline.obj  
#include <stdio.h>  
struct _load_config_used {  
   void Test();  
   void Test2() { printf("in Test2\n"); }  
};  
  
void _load_config_used::Test() { printf("in Test\n"); }  
```  
  
 Y, a continuación,  
  
```  
// LNK2019_function_inline_2.cpp  
// compile with: LNK2019_function_inline.lib  
struct _load_config_used {  
   void Test();  
   void Test2();  
};  
  
int main() {  
   _load_config_used x;  
   x.Test();  
   x.Test2();   // LNK2019  
}  
```  
  
 Si utiliza la directiva del compilador `#pragma inline_depth`, asegúrese de que tiene un valor de 2 o un conjunto superior.  Un valor igual a cero desactiva la inclusión de funciones en línea.  También debe asegurarse de que está utilizando las opciones del compilador **\/Ob1** o **\/Ob2**.  
  
 Mezclar opciones de compilación en línea y no en línea en módulos diferentes puede causar el error LNK2001.  Si se crea una biblioteca de C\+\+ con la inclusión de funciones en línea activada \([\/Ob1](../../build/reference/ob-inline-function-expansion.md) u [\/Ob2](../../build/reference/ob-inline-function-expansion.md)\) pero el archivo de encabezado correspondiente que describe las funciones la tiene desactivada \(no hay ninguna opción\), se obtiene el error LNK2001.  No se insertan las funciones en línea en el código a partir del archivo de encabezado, pero, al no encontrarse en el archivo de biblioteca, no hay dirección para resolver la diferencia.  
  
 Igualmente, un proyecto que utilice la inclusión de funciones en línea, pero que defina las funciones en un archivo .cpp en lugar de en el archivo de encabezado, también generará el error LNK2019.  El archivo de encabezado se incluye en cualquier lugar donde se considere apropiado, pero las funciones sólo se incluyen cuando el archivo .cpp pasa por el compilador; por tanto, el vinculador ve las funciones como símbolos externos no resueltos al utilizarse en otros módulos.  
  
```  
// LNK2019_FIP.h  
struct testclass {  
   void PublicStatMemFunc1(void);  
};  
```  
  
 y, a continuación,  
  
```  
// LNK2019_FIP.cpp  
// compile with: /c  
#include "LNK2019_FIP.h"  
inline void testclass::PublicStatMemFunc1(void) {}  
```  
  
 y, a continuación,  
  
```  
// LNK2019_FIP_2.cpp  
// compile with: LNK2019_FIP.cpp  
// LNK2019 expected  
#include "LNK2019_FIP.h"  
int main() {  
   testclass testclsObject;  
  
   // module cannot see the implementation of PublicStatMemFunc1  
   testclsObject.PublicStatMemFunc1();  
}  
```  
  
## Vea también  
 [Error de las herramientas del vinculador LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)