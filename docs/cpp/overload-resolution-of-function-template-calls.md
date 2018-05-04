---
title: Resolución de sobrecargas de llamadas de plantilla de función | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function templates overload resolution
ms.assetid: a2918748-2cbb-4fc6-a176-e256f120bee4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d4a0e2867c5057eb5808c4d39687961eabba6dd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="overload-resolution-of-function-template-calls"></a>Resolución de sobrecarga de llamadas de plantilla de función
Una plantilla de función puede sobrecargar funciones que no son de plantilla con el mismo nombre. En este escenario, las llamadas a función se resuelven utilizando primero la deducción de argumento de plantilla para crear instancias de la plantilla de función con una especialización exclusiva. Si la deducción de argumento de plantilla no se produce correctamente, se considera que las demás sobrecargas de función resuelven la llamada. Estas otras sobrecargas, también conocidas como conjunto de candidato, incluyen funciones que no son de plantilla y otras plantillas de función de las que se pueden crear instancias. Si la deducción de argumento de plantilla se realiza correctamente, la función generada se compara con las demás funciones para determinar la mejor coincidencia, de acuerdo con las reglas para la resolución de sobrecarga. Para obtener más información, consulte [sobrecarga de funciones](function-overloading.md).  
  
## <a name="example"></a>Ejemplo

 Si una función que no es de plantilla constituye una coincidencia igualmente buena con una función de plantilla, se elige la primera (a menos que los argumentos de plantilla estén especificados explícitamente), como en la llamada a `f(1, 1)` en el ejemplo siguiente.  
  
```cpp
// template_name_resolution9.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
void f(int, int) { cout << "f(int, int)" << endl; }  
void f(char, char) { cout << "f(char, char)" << endl; }  
  
template <class T1, class T2>  
void f(T1, T2)  
{  
   cout << "void f(T1, T2)" << endl;  
};  
  
int main()  
{  
   f(1, 1);   // Equally good match; choose the nontemplate function.  
   f('a', 1); // Chooses the template function.  
   f<int, int>(2, 2);  // Template arguments explicitly specified.  
}  
```  
  
```Output  
f(int, int)  
void f(T1, T2)  
void f(T1, T2)  
```  
  
## <a name="example"></a>Ejemplo

 En el ejemplo siguiente se muestra que se prefiere la función de plantilla que coincide exactamente si la función que no es de plantilla requiere una conversión.  
  
```cpp
// template_name_resolution10.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
void f(int, int) { cout << "f(int, int)" << endl; }  
  
template <class T1, class T2>  
void f(T1, T2)  
{  
   cout << "void f(T1, T2)" << endl;  
};  
  
int main()  
{  
   long l = 0;  
   int i = 0;  
   // Call the template function f(long, int) because f(int, int)  
   // would require a conversion from long to int.  
   f(l, i);  
}  
```  
  
```Output  
void f(T1, T2)  
```  
  
## <a name="see-also"></a>Vea también

 [Resolución de nombres](../cpp/templates-and-name-resolution.md)   
 [typename](../cpp/typename.md)   
 
