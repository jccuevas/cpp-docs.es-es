---
title: Sobrecargar el operador &lt;&lt; para las clases propias | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- operator<<, overloading for your own classes
- operator <<, overloading for your own classes
ms.assetid: ad1d2c49-d84e-48a8-9c09-121f28b10bf0
caps.latest.revision: 12
author: corob-msft
ms.author: corob
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 22eb3fbef373c2e80989c49887cfa8b3c9eadc61
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="overloading-the-ltlt-operator-for-your-own-classes"></a>Sobrecargar el operador &lt;&lt; para las clases propias
Los flujos de salida usan el operador de inserción (`<<`) para los tipos estándar. También puede sobrecargar el operador `<<` para sus propias clases.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de la función `write` se ha mostrado el uso de una estructura `Date`. Una fecha es un candidato ideal para una clase de C++ en la que los miembros de fecha (mes, día y año) se ocultan de la vista. Un flujo de salida es el destino lógico para mostrar dicha estructura. Este código muestra una fecha con el objeto `cout`:  
  
```  
Date dt(1, 2, 92);

cout <<dt;  
```  
  
 Para conseguir que `cout` acepte un objeto `Date` después del operador de inserción, sobrecargue el operador de inserción para que reconozca un objeto `ostream` a la izquierda y `Date` a la derecha. La función de operador `<<` sobrecargada debe declararse después como un elemento de confianza de la clase `Date`, de manera que pueda tener acceso a los datos privados de un objeto `Date`.  
  
```  
// overload_date.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
class Date  
{  
    int mo, da, yr;  
public:  
    Date(int m, int d, int y)  
    {  
        mo = m; da = d; yr = y;  
    }  
    friend ostream& operator<<(ostream& os, const Date& dt);  
};  
  
ostream& operator<<(ostream& os, const Date& dt)  
{  
    os << dt.mo << '/' << dt.da << '/' << dt.yr;  
    return os;  
}  
  
int main()  
{  
    Date dt(5, 6, 92);  
    cout << dt;  
}  
```  
  
```Output  
5/6/92  
```  
  
## <a name="remarks"></a>Comentarios  
 El operador sobrecargado devuelve una referencia al objeto `ostream` original, que significa que puede combinar inserciones:  
  
```  
cout <<"The date is" <<dt <<flush;  
```  
  
## <a name="see-also"></a>Vea también  
 [Flujos de salida](../standard-library/output-streams.md)


