---
title: "Resolución de sobrecargas de llamadas de plantilla de función | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function templates overload resolution
ms.assetid: a2918748-2cbb-4fc6-a176-e256f120bee4
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: f460497071445cff87308fa9bf6e0d43c6f13a3e
ms.openlocfilehash: f5c4a8e6392bc5b4338738b56099adac268e7af1
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

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
 

