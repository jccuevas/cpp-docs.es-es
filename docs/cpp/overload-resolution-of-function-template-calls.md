---
title: "Resoluci&#243;n de sobrecarga de llamadas de plantilla de funci&#243;n | Microsoft Docs"
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
  - "resolución de sobrecarga de plantillas de función"
ms.assetid: a2918748-2cbb-4fc6-a176-e256f120bee4
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Resoluci&#243;n de sobrecarga de llamadas de plantilla de funci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una plantilla de función puede sobrecargar funciones que no son de plantilla con el mismo nombre.  En este escenario, las llamadas a función se resuelven utilizando primero la deducción de argumento de plantilla para crear instancias de la plantilla de función con una especialización exclusiva.  Si la deducción de argumento de plantilla no se produce correctamente, se considera que las demás sobrecargas de función resuelven la llamada.  Estas otras sobrecargas, también conocidas como conjunto de candidato, incluyen funciones que no son de plantilla y otras plantillas de función de las que se pueden crear instancias.  Si la deducción de argumento de plantilla se realiza correctamente, la función generada se compara con las demás funciones para determinar la mejor coincidencia, de acuerdo con las reglas para la resolución de sobrecarga.  Para obtener más información, vea [Sobrecarga](../misc/overloading-cpp.md) y [Coincidencia de argumentos](../misc/argument-matching.md).  
  
## Ejemplo  
 Si una función que no es de plantilla constituye una coincidencia igualmente buena con una función de plantilla, se elige la primera \(a menos que los argumentos de plantilla estén especificados explícitamente\), como en la llamada a `f(1, 1)` en el ejemplo siguiente.  
  
```  
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
  
  **f\(int, int\)**  
**void f\(T1, T2\)**  
**void f\(T1, T2\)**   
## Ejemplo  
 En el ejemplo siguiente se muestra que se prefiere la función de plantilla que coincide exactamente si la función que no es de plantilla requiere una conversión.  
  
```  
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
  
  **void f\(T1, T2\)**   
## Vea también  
 [Resolución de nombres](../cpp/templates-and-name-resolution.md)   
 [typename](../cpp/typename.md)   
 [Deducción de argumentos de plantilla](../Topic/Template%20Argument%20Deduction.md)