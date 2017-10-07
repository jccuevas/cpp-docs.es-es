---
title: "Argumentos de función de tipo de referencia | Documentos de Microsoft"
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
- arguments [C++], function
- functions [C++], paramters
- function parameters [C++], reference-type
- function arguments [C++], reference-type
- passing parameters [C++], reference-type arguments
ms.assetid: 0a70e831-9e76-46c0-821d-aeba13d73cc0
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: e74cbde44cad618720983fbda4a6cf9ce8b75dc1
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="reference-type-function-arguments"></a>Argumentos de función de tipo de referencia
Suele ser más eficaz pasar referencias, en lugar de objetos grandes, a las funciones. De este modo, el compilador puede pasar la dirección del objeto mientras mantiene la sintaxis que se habría utilizado para tener acceso al objeto. Considere el ejemplo siguiente, en el que se usa la estructura `Date`:  
  
```  
// reference_type_function_arguments.cpp  
struct Date  
{  
short DayOfWeek;  
short Month;  
short Day;  
short Year;  
};  
  
// Create a Julian date of the form DDDYYYY  
// from a Gregorian date.  
long JulianFromGregorian( Date& GDate )  
{  
static int cDaysInMonth[] = {  
31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31  
   };  
long JDate = 0;  
// Add in days for months already elapsed.  
for ( int i = 0; i < GDate.Month - 1; ++i )  
JDate += cDaysInMonth[i];  
// Add in days for this month.  
JDate += GDate.Day;  
  
// Check for leap year.  
if ( GDate.Year % 100 != 0 && GDate.Year % 4 == 0 )  
JDate++;  
// Add in year.  
JDate *= 10000;  
JDate += GDate.Year;  
  
return JDate;  
}  
  
int main()  
{  
}  
```  
  
 El código anterior muestra que se accede a los miembros de una estructura pasada por referencia mediante el operador de selección de miembro (**.**) en lugar del operador de selección de miembro de puntero (**->**).  
  
 Aunque los argumentos pasados como tipos de referencia rigen por la sintaxis de los tipos de no son de puntero, mantienen una característica importante de los tipos de puntero: son modificables a menos que se declara como **const**. Dado que el código anterior no tenía como intención modificar el objeto `GDate`, un prototipo de función más adecuado sería:  
  
```  
long JulianFromGregorian( const Date& GDate );  
```  
  
 Este prototipo garantiza que la función `JulianFromGregorian` no cambiará su argumento.  
  
 Cualquier función prototipo que toma un tipo de referencia puede aceptar un objeto del mismo tipo en su lugar, porque no hay una conversión estándar de *typename* a *typename* ** & **.  
  
## <a name="see-also"></a>Vea también  
 [Referencias](../cpp/references-cpp.md)
