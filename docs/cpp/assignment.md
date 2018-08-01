---
title: Asignación | Microsoft Docs
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
ms.openlocfilehash: c6343d7be23e633fe383343bd7f154d5cc9bb234
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407616"
---
# <a name="assignment"></a>Asignación
El operador de asignación (**=**), en realidad, es un operador binario. La declaración es idéntica a cualquier otro operador binario, con las excepciones siguientes:  
  
-   Debe ser una función miembro no estática. No **operador =** se pueden declarar como una función no miembro.  
  
-   Las clases derivadas no lo heredan.  
  
-   Valor predeterminado es **operador =** función puede generarse por el compilador para los tipos de clase si no existe ninguno.  
  
 El ejemplo siguiente muestra cómo declarar un operador de asignación:  
  
```cpp 
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
  
```cpp 
pt1 = pt2 = pt3;  
```  
  
## <a name="see-also"></a>Vea también  
 [Sobrecarga de operadores](../cpp/operator-overloading.md)