---
title: "Usar extern para especificar la vinculaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "extern"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "declaraciones, externos"
  - "extern (palabra clave) [C++], vinculación a funciones no de C++"
  - "vinculación externa, extern (modificador)"
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Usar extern para especificar la vinculaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
        extern string-literal { declaration-list }  
extern string-literal declaration  
```  
  
## Comentarios  
 La palabra clave `extern` declara una variable o función, y especifica que tiene una vinculación externa \(su nombre está visible desde archivos distintos del que la define\).  Al modificar una variable, `extern` especifica que la variable tiene duración estática \(se asigna cuando se inicia el programa y se desasigna cuando finaliza el programa\).  La variable o función se puede definir en otro archivo de código fuente, o más adelante en el mismo archivo.  Las declaraciones de variables y funciones en el ámbito de archivo son externas de forma predeterminada.  
  
## Ejemplo  
  
```  
// specifying_linkage1.cpp  
int i = 1;  
void other();  
  
int main() {  
   // Reference to i, defined above:  
   extern int i;  
}  
  
void other() {  
   // Address of global i assigned to pointer variable:  
   static int *external_i = &i;  
  
   // i will be redefined; global i no longer visible:  
   // int i = 16;  
}  
```  
  
 En C\+\+, cuando se usa con una cadena, `extern` especifica el uso de las convenciones de vinculación de otro lenguaje para los declaradores.  Las funciones y datos de C solo están accesibles si se declaran previamente con vinculación de C.  Sin embargo, se deben definir en una unidad de traducción compilada por separado.  
  
 Microsoft C\+\+ admite las cadenas **"C"** y **"C\+\+"** en el campo de *string\-literal*.  Todos los archivos de inclusión estándar utilizan la sintaxis de `extern` de “C” para permitir que las funciones de la biblioteca en tiempo de ejecución se usen en programas de C\+\+.  
  
## Ejemplo  
 En el ejemplo siguiente se muestran maneras alternativas de declarar los nombres que tienen vinculación de C:  
  
```  
// specifying_linkage2.cpp  
// compile with: /c  
// Declare printf with C linkage.  
extern "C" int printf( const char *fmt, ... );  
  
//  Cause everything in the specified header files  
//   to have C linkage.  
extern "C" {  
   // add your #include statements here  
   #include <stdio.h>  
}  
  
//  Declare the two functions ShowChar and GetChar  
//   with C linkage.  
extern "C" {  
   char ShowChar( char ch );  
   char GetChar( void );  
}  
  
//  Define the two functions ShowChar and GetChar  
//   with C linkage.  
extern "C" char ShowChar( char ch ) {  
   putchar( ch );  
   return ch;  
}  
  
extern "C" char GetChar( void ) {  
   char ch;  
  
   ch = getchar();  
   return ch;  
}  
  
// Declare a global variable, errno, with C linkage.  
extern "C" int errno;  
```  
  
 Si una función tiene más de una especificación de vinculación, deben coincidir; es un error declarar funciones que tengan tanto vinculación de C como de C\+\+.  Además, si en un programa aparecen dos declaraciones para una función \(una con una especificación de vinculación y otra sin ella\), la declaración con especificación de vinculación debe ser la primera.  Cualquier declaración redundante de funciones que ya tengan especificación de vinculación recibe la vinculación especificada en la primera declaración.  Por ejemplo:  
  
```  
extern "C" int CFunc1();  
...  
int CFunc1();            // Redeclaration is benign; C linkage is  
                         //  retained.  
  
int CFunc2();  
...  
extern "C" int CFunc2(); // Error: not the first declaration of  
                         //  CFunc2;  cannot contain linkage  
                         //  specifier.  
```  
  
 Las funciones y objetos declarados explícitamente como **static** dentro del cuerpo de un especificador de vinculación compuesto \(**{ }**\) se tratan como funciones u objetos estáticos; el especificador de vinculación se omite.  Otras funciones y objetos se comportan como si se hubieran declarado mediante la palabra clave `extern`.  \(Vea [Uso de extern para especificar vinculación](../cpp/using-extern-to-specify-linkage.md) para obtener más información sobre la palabra clave `extern`\).  
  
## Vea también  
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [\(NOTINBUILD\)Linkage Specifications](http://msdn.microsoft.com/es-es/d2b0cff1-7798-4c38-9ac8-61c3bfe2bfb9)   
 [extern \(Especificador de clase de almacenamiento\)](../c-language/extern-storage-class-specifier.md)   
 [Comportamiento de los identificadores](../c-language/behavior-of-identifiers.md)   
 [Vinculación](../c-language/linkage.md)