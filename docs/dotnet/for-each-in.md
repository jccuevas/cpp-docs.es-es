---
title: "for each, in | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::foreach"
  - "for"
  - "each"
  - "in"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "foreach (palabra clave) [C++]"
ms.assetid: 0c3a364b-2747-43f3-bb8d-b7d3b7023f79
caps.latest.revision: 24
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# for each, in
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Procesa una iteración a través de una matriz o colección.  Esta palabra clave no estándar está disponible en C\+\+\/CLI y proyectos nativos de C\+\+.  Sin embargo, no se recomienda su uso.  Considere la posibilidad de utilizar un [Instrucción for basada en intervalo \(C\+\+\)](../cpp/range-based-for-statement-cpp.md) estándar en su lugar.  
  
## Todos los runtimes  
 **Sintaxis**  
  
```  
  
        for each (type identifier in expression) {  
   statements  
}  
  
```  
  
 **Parámetros**  
  
 `type`  
 Tipo de `identifier`.  
  
 `identifier`  
 Variable de iteración que representa el elemento de la colección.  Cuando `identifier` es un [Operador de referencia de seguimiento](../windows/tracking-reference-operator-cpp-component-extensions.md), puede modificar el elemento.  
  
 `expression`  
 Colección o expresión de matriz.  El elemento de la colección debe ser de un tipo que el compilador pueda convertir en el tipo `identifier`.  
  
 `statements`  
 Instrucción o instrucciones que se van a ejecutar.  
  
 **Comentarios**  
  
 La instrucción `for each` se utiliza para procesar una iteración en una colección.  Puede modificar los elementos de una colección, pero no puede agregar ni eliminar elementos.  
  
 Las instrucciones *statements* se ejecutan para cada elemento de la matriz o colección.  Cuando la iteración se ha completado en todos los elementos de la colección, el control se transfiere a la instrucción que sigue al bloque `for each`.  
  
 `for each` e `in` son [palabras clave contextuales](../windows/context-sensitive-keywords-cpp-component-extensions.md).  
  
 Para obtener más información:  
  
-   [Iterar por una colección STL mediante for each](../dotnet/iterating-over-stl-collection-by-using-for-each.md)  
  
-   [Cómo: Iterar por matrices con for each](../dotnet/how-to-iterate-over-arrays-with-for-each.md)  
  
-   [Cómo: Iterar por una colección genérica con for each](../dotnet/how-to-iterate-over-a-generic-collection-with-for-each.md)  
  
-   [Cómo: Iterar por una colección definida por el usuario con for each](../dotnet/how-to-iterate-over-a-user-defined-collection-with-for-each.md)  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
  
### Requisitos  
 Opción del compilador: **\/ZW**  
  
### Ejemplo  
 En este ejemplo se muestra cómo se usa `for each` para procesar una iteración en una cadena.  
  
```  
// for_each_string1.cpp  
// compile with: /ZW  
#include <stdio.h>  
using namespace Platform;  
  
ref struct MyClass {  
   property String^ MyStringProperty;  
};  
  
int main() {  
   String^ MyString = ref new String("abcd");  
  
   for each ( char c in MyString )  
      wprintf("%c", c);  
  
   wprintf("/n");  
  
   MyClass^ x = ref new MyClass();  
   x->MyStringProperty = "Testing";  
  
   for each( char c in x->MyStringProperty )  
      wprintf("%c", c);  
}  
```  
  
 **Salida**  
  
  **abcd**  
 **Pruebas**   
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **Comentarios**  
  
 La sintaxis de CLR es igual que la de **todos los runtimes**, excepto por lo siguiente.  
  
 *expression*  
 Expresión o colección de matriz administrada.  El elemento de la colección debe ser de un tipo que el compilador pueda convertir de <xref:System.Object> al tipo *identifier*.  
  
 *expression* se evalúa como un tipo que implementa <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601> o un tipo que define un método `GetEnumerator` que devuelve un tipo que implementa <xref:System.Collections.IEnumerator> o declara todos los métodos definidos en `IEnumerator`.  
  
### Requisitos  
 Opción del compilador: **\/clr**  
  
### Ejemplo  
 En este ejemplo se muestra cómo se usa `for each` para procesar una iteración en una cadena.  
  
```  
// for_each_string2.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct MyClass {  
   property String ^ MyStringProperty;  
};  
  
int main() {  
   String ^ MyString = gcnew String("abcd");  
  
   for each ( Char c in MyString )  
      Console::Write(c);  
  
   Console::WriteLine();  
  
   MyClass ^ x = gcnew MyClass();  
   x->MyStringProperty = "Testing";  
  
   for each( Char c in x->MyStringProperty )  
      Console::Write(c);  
}  
```  
  
 **Salida**  
  
  **abcd**  
 **Pruebas**    
## Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)