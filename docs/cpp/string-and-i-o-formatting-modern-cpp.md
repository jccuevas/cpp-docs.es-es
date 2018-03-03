---
title: Cadena y I-O formato (C++ moderno) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a13861fe03547e37c4de72c21a528e297a217511
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="string-and-io-formatting-modern-c"></a>Formato de cadena y de E/S (C++ moderno)
C++ [iostreams](../standard-library/iostream.md) tienen la capacidad de E/S de cadena con formato. Por ejemplo, el código siguiente muestra cómo establecer cout para dar formato a un número entero y de salida en formato hexadecimal, en primer lugar guardar desactivar el estado actual y volver a configurar posteriormente, porque una vez que el formato de estado pasa a cout, permanece de este modo hasta que se modifiquen, no solo para una línea de código.  
  
```cpp  
#include <iostream>  
#include <iomanip>  
  
using namespace std;  
  
int main()   
{  
    ios state(nullptr);  
  
    cout << "The answer in decimal is: " << 42 << endl;  
  
    state.copyfmt(cout); // save current formatting  
    cout << "In hex: 0x" // now load up a bunch of formatting modifiers  
        << hex   
        << uppercase   
        << setw(8)   
        << setfill('0')   
        << 42            // the actual value we wanted to print out  
        << endl;  
    cout.copyfmt(state); // restore previous formatting  
}  
  
```  
  
 Esto puede ser completamente demasiado complicada en muchos casos. Como alternativa, puede utilizar Boost.Format desde las bibliotecas de C++ de aumento, aunque no es estándar. Puede descargar cualquier biblioteca de aumento de la [aumento](http://www.boost.org/) sitio Web.  
  
 Algunas ventajas de Boost.Format son:  
  
-   Seguridad: Seguridad de tipos y produce una excepción si hay errores, por ejemplo, la especificación de muy pocos o demasiados elementos.  
  
-   Extensible: Funciona con cualquier tipo que se puede transmitir.  
  
-   Cómoda: Posix estándar y las cadenas de formato similar.  
  
 Aunque Boost.Format se basa en C++ [iostreams](../standard-library/iostream-programming.md), que son seguros y extensible, no son con optimización para el rendimiento. Cuando necesite optimizar el rendimiento, considere la posibilidad de C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) y [sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), que son rápida y fácil de usar. Sin embargo, no son extensibles o segura ante las vulnerabilidades. (Existen versiones seguras, pero también implican una ligera disminución del rendimiento. Para obtener más información, consulte [printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md) y [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)).  
  
 El código siguiente muestra algunas de la características de formato de aumento.  
  
```cpp  
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );  
    // s contains "hello hello world"    
  
    for( auto i = 0; i < names.size(); ++i )  
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];  
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789  
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Aquí está otra vez C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)   
 [Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)   
 [\<iostream >](../standard-library/iostream.md)   
 [\<límites >](../standard-library/limits.md)   
 [\<iomanip>](../standard-library/iomanip.md)
