---
title: "Tipos de clase an&#243;nima | Microsoft Docs"
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
  - "tipos de clases anónimos"
  - "tipos de clase, anónimos"
ms.assetid: 9ba667b2-8c2a-4c29-82a6-fa120b9233c8
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Tipos de clase an&#243;nima
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las clases pueden ser anónimas, es decir, se pueden declarar sin un *identificador*.  Esto es útil cuando se reemplaza un nombre de clase con un nombre `typedef`, como en el siguiente ejemplo de código:  
  
```  
typedef struct  
{  
    unsigned x;  
    unsigned y;  
} POINT;  
```  
  
> [!NOTE]
>  El uso de las clases anónimas que se muestra en el ejemplo anterior es útil para mantener la compatibilidad con el código de C existente.  En algún código de C, el uso de `typedef` junto con estructuras anónimas es frecuente.  
  
 Las clases anónimas también son útiles cuando se desea que una referencia a un miembro de clase aparezca como si no estuviera contenida en una clase independiente, como en el siguiente ejemplo de código:  
  
```  
struct PTValue  
{  
    POINT ptLoc;  
    union  
    {  
        int  iValue;  
        long lValue;  
    };  
};  
  
PTValue ptv;  
```  
  
 En el código anterior, se puede obtener acceso a `iValue` usando el operador de selección de miembros de objeto \(**.**\) del modo siguiente:  
  
```  
int i = ptv.iValue;  
```  
  
 Las clases anónimas están sujetas a determinadas restricciones.  \(Para obtener más información sobre las uniones anónimas, vea [Uniones](../cpp/unions.md)\). Las clases anónimas:  
  
-   No pueden tener un constructor o un destructor.  
  
-   No se pueden pasar como argumentos a funciones \(a menos que la comprobación de tipos se rechace mediante el uso de puntos suspensivos\).  
  
-   No se pueden devolver como valores devueltos de funciones.  
  
## Structs anónimos  
  
### Específicos de Microsoft  
 Una extensión de Microsoft C permite declarar una variable de estructura dentro de otra estructura sin darle un nombre.  Estas estructuras anidadas se denominan estructuras anónimas.  C\+\+ no permite estructuras anónimas.  
  
 Puede tener acceso a los miembros de una estructura anónima como si fueran miembros de la estructura contenedora.  
  
```  
// anonymous_structures.c  
#include <stdio.h>  
  
struct phone  
{  
    int  areacode;  
    long number;  
};  
  
struct person  
{  
    char   name[30];  
    char   gender;  
    int    age;  
    int    weight;  
    struct phone;    // Anonymous structure; no name needed  
} Jim;  
  
int main()  
{  
    Jim.number = 1234567;  
    printf_s("%d\n", Jim.number);     
}  
//Output: 1234567  
```  
  
### FIN de Específicos de Microsoft  
  
## Vea también  
 [\(NOTINBUILD\) Defining Class Types](http://msdn.microsoft.com/es-es/e8c65425-0f3a-4dca-afc2-418c3b1e57da)