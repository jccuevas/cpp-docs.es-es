---
title: "Formato de cadena y de E/S (C++ moderno) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Formato de cadena y de E/S (C++ moderno)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[iostreams](../standard-library/iostream.md) de C\+\+ admiten cadena con formato E\/S.  Por ejemplo, el código siguiente muestra cómo establecer cout para dar formato a un entero y así generarlo como hexadecimal, guardándolo en primer guardar fuera del estado actual y estableciéndolo de nuevo después, ya que una vez que el formato de estado se pasa a cout, permanece así hasta que se cambie, no solo para la única línea de código.  
  
```fortran  
#include <iostream>  
#include <iomanip>  
  
using namespace std;  
  
int main()   
{  
    ios state(nullptr);  
  
    cout << "The answer in decimal is: " << 42 << endl;  
  
    state.copyfmt(cout); // save current formatting  
    cout << "In hex: 0x" // now load up a bunch of formatting modifiers  
        << hex   
        << uppercase   
        << setw(8)   
        << setfill('0')   
        << 42            // the actual value we wanted to print out  
        << endl;  
    cout.copyfmt(state); // restore previous formatting  
}  
  
```  
  
 Esto puede ser demasiado complejo en muchos casos.  Como alternativa, puede utilizar Boost.Format de las bibliotecas Boost de C\+\+, aunque no sea estándar.  Puede descargar cualquier biblioteca de Boost desde el sitio web de [Boost](http://www.boost.org/).  
  
 Algunas ventajas de Boost.Format son:  
  
-   Seguro: seguro de tipos y produce una excepción para errores; por ejemplo, la especificación de muy pocos elementos o de demasiados elementos.  
  
-   Extensible: funciona para cualquier tipo con el que se pueda hacer streaming.  
  
-   Adecuado: Posix estándar y cadenas de formato similares.  
  
 Aunque Boost.Format está compilado en C\+\+ [iostreams](../standard-library/iostream-programming.md), de forma segura y extensible, no están optimizados para su rendimiento.  Al requerir la optimización del rendimiento, considere [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) y [sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) de C, que son rápidos y fáciles de usar.  Sin embargo, no son extensibles ni están seguros ante vulnerabilidades. \(Las versiones seguras existen, pero incurren en una ligera disminución del rendimiento.  Para obtener más información, vea [printf\_s, \_printf\_s\_l, wprintf\_s, \_wprintf\_s\_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md) y [sprintf\_s, \_sprintf\_s\_l, swprintf\_s, \_swprintf\_s\_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md).  
  
 El código siguiente muestra algunas de las características de formato de Boost.  
  
```cpp  
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );  
    // s contains "hello hello world"    
  
    for( auto i = 0; i < names.size(); ++i )  
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];  
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789  
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321  
  
```  
  
## Vea también  
 [Aquí está otra vez C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referencia de lenguaje C\+\+](../cpp/cpp-language-reference.md)   
 [Biblioteca estándar de C\+\+](../standard-library/cpp-standard-library-reference.md)   
 [\<iostream\>](../standard-library/iostream.md)   
 [\<limits\>](../standard-library/limits.md)   
 [\< iomanip \>](../standard-library/iomanip.md)