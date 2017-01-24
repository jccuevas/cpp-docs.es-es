---
title: "Sobrecargar el operador &lt;&lt; para las clases propias | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operador <<, sobrecargar para las clases propias"
  - "operator<<, sobrecargar para las clases propias"
ms.assetid: ad1d2c49-d84e-48a8-9c09-121f28b10bf0
caps.latest.revision: 12
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Sobrecargar el operador &lt;&lt; para las clases propias
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las secuencias de salida usan el operador de inserción \(`<<`\) para los tipos estándar.  También puede sobrecargar el operador de `<<` dispone de clases.  
  
## Ejemplo  
 El ejemplo de función de `write` ilustra el uso de una estructura de `Date` .  Una fecha es un candidato ideal a la clase en cuestión. en la que oculta para los miembros de datos \(mes, día, y año\) de la vista.  Una secuencia de salida es el destino lógico para mostrar esa estructura.  Este código muestra una fecha con el objeto de `cout` :  
  
```  
Date dt( 1, 2, 92 );  
cout << dt;  
```  
  
 Para obtener `cout` acepte un objeto de `Date` después del operador de inserción, sobrecargue el operador de inserción para reconocer un objeto de `ostream` a la izquierda y `Date` a la derecha.  La función sobrecargada de operador de `<<` deberá declararse como una función friend de la clase `Date` para que se puede tener acceso a los datos privados de un objeto de `Date` .  
  
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
  
  **5\/6\/92**   
## Comentarios  
 El operador sobrecargado devuelve una referencia al objeto original de `ostream` , que significa que puede combinar inserciones:  
  
```  
cout << "The date is" << dt << flush;  
```  
  
## Vea también  
 [Flujos de salida](../standard-library/output-streams.md)