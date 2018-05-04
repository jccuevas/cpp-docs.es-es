---
title: Asignación | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], overloaded
ms.assetid: d87e4f89-f8f5-42c1-9d3c-184bca9d0e15
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66fd08215c3849bf487578b28b1824afbec14c52
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="assignment"></a>Asignación
El operador de asignación (**=**), en sentido estricto, es un operador binario. La declaración es idéntica a cualquier otro operador binario, con las excepciones siguientes:  
  
-   Debe ser una función miembro no estática. Ningún `operator=` se puede declarar como función no miembro.  
  
-   Las clases derivadas no lo heredan.  
  
-   El compilador puede generar una función `operator=` predeterminada para los tipos de clase si no existe ninguna. (Para obtener más información sobre predeterminado `operator=` funciones, vea [miembro a miembro asignación e inicialización](http://msdn.microsoft.com/en-us/94048213-8b49-4416-8069-b1b7a6f271f9).)  
  
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
  
 Observe que el argumento proporcionado es el lado derecho de la expresión. El operador devuelve el objeto para preservar el comportamiento del operador de asignación, que devuelve el valor del lado izquierdo después de que se complete la asignación. Esto permite escribir instrucciones tales como:  
  
```  
pt1 = pt2 = pt3;  
```  
  
## <a name="see-also"></a>Vea también  
 [Sobrecarga de operadores](../cpp/operator-overloading.md)