---
title: "Argumentos de funci&#243;n de tipo de referencia | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "argumentos [C++], función"
  - "argumentos de función, tipo de referencia"
  - "parámetros de la función, tipo de referencia"
  - "funciones [C++], parámetros"
  - "pasar parámetros, argumentos de tipo de referencia"
ms.assetid: 0a70e831-9e76-46c0-821d-aeba13d73cc0
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Argumentos de funci&#243;n de tipo de referencia
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Suele ser más eficaz pasar referencias, en lugar de objetos grandes, a las funciones.  De este modo, el compilador puede pasar la dirección del objeto mientras mantiene la sintaxis que se habría utilizado para tener acceso al objeto.  Considere el ejemplo siguiente, en el que se usa la estructura `Date`:  
  
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
  
 El código anterior muestra que, para acceder a los miembros de una estructura pasada por referencia, se usa el operador de selección de miembro \(**.**\) en lugar del operador de selección de miembro de puntero \(**–\>**\).  
  
 Aunque los argumentos pasados como tipos de referencia se rigen por la sintaxis de los tipos que no son de puntero, mantienen una característica importante de los tipos de puntero: son modificables a menos que se declaren como **const**.  Dado que el código anterior no tenía como intención modificar el objeto `GDate`, un prototipo de función más adecuado sería:  
  
```  
long JulianFromGregorian( const Date& GDate );  
```  
  
 Este prototipo garantiza que la función `JulianFromGregorian` no cambiará su argumento.  
  
 Cualquier función que se ajuste a un prototipo que toma un tipo de referencia puede aceptar un objeto del mismo tipo en su lugar, porque hay una conversión estándar de *typename* a *typename***&**.  
  
## Vea también  
 [Referencias](../cpp/references-cpp.md)