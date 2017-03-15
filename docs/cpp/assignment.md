---
title: "Asignaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operadores de asignación, sobrecargados"
  - "operadores [C++], asignación"
ms.assetid: d87e4f89-f8f5-42c1-9d3c-184bca9d0e15
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Asignaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El operador de asignación \(**\=**\) es, en rigor, un operador binario.  La declaración es idéntica a cualquier otro operador binario, con las excepciones siguientes:  
  
-   Debe ser una función miembro no estática.  Ningún `operator=` se puede declarar como función no miembro.  
  
-   Las clases derivadas no lo heredan.  
  
-   El compilador puede generar una función `operator=` predeterminada para los tipos de clase si no existe ninguna. \(Para obtener más información sobre las funciones `operator=` predeterminadas, vea [Asignación e inicialización miembro a miembro](http://msdn.microsoft.com/es-es/94048213-8b49-4416-8069-b1b7a6f271f9)\).  
  
 El ejemplo siguiente muestra cómo declarar un operador de asignación:  
  
```  
// assignment.cpp  
class Point  
{  
public:  
   Point &operator=( Point & );  // Right side is the argument.  
   int _x, _y;  
};  
  
// Define assignment operator.  
Point &Point::operator=( Point &ptRHS )  
{  
   _x = ptRHS._x;  
   _y = ptRHS._y;  
  
   return *this;  // Assignment operator returns left side.  
}  
  
int main()  
{  
}  
```  
  
 Observe que el argumento proporcionado es el lado derecho de la expresión.  El operador devuelve el objeto para preservar el comportamiento del operador de asignación, que devuelve el valor del lado izquierdo después de que se complete la asignación.  Esto permite escribir instrucciones tales como:  
  
```  
pt1 = pt2 = pt3;  
```  
  
## Vea también  
 [Sobrecarga de operadores](../cpp/operator-overloading.md)