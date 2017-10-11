---
title: "Tipos de clase anónima | Documentos de Microsoft"
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
- class types [C++], anonymous
- anonymous class types
ms.assetid: 9ba667b2-8c2a-4c29-82a6-fa120b9233c8
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 29313d499f7459175c9dc2331148cdd6401e5e53
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="anonymous-class-types"></a>Tipos de clase anónima
Las clases pueden ser anónimas, es decir, se pueden declarar sin un *identificador*. Esto es útil cuando se reemplaza un nombre de clase con un nombre `typedef`, como en el siguiente ejemplo de código:  
  
```  
typedef struct  
{  
    unsigned x;  
    unsigned y;  
} POINT;  
```  
  
> [!NOTE]
>  El uso de las clases anónimas que se muestra en el ejemplo anterior es útil para mantener la compatibilidad con el código de C existente. En algún código de C, el uso de `typedef` junto con estructuras anónimas es frecuente.  
  
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
  
 En el código anterior, `iValue` puede tener acceso mediante el operador de selección de miembro de objeto (**.**) como se indica a continuación:  
  
```  
int i = ptv.iValue;  
```  
  
 Las clases anónimas están sujetas a determinadas restricciones. (Para obtener más información sobre las uniones anónimas, vea [uniones](../cpp/unions.md).) Las clases anónimas:  
  
-   No pueden tener un constructor o un destructor.  
  
-   No se pueden pasar como argumentos a funciones (a menos que la comprobación de tipos se rechace mediante el uso de puntos suspensivos).  
  
-   No se pueden devolver como valores devueltos de funciones.  
  
## <a name="anonymous-structs"></a>Structs anónimos  
  
### <a name="microsoft-specific"></a>Específicos de Microsoft  
 Una extensión de Microsoft C permite declarar una variable de estructura dentro de otra estructura sin darle un nombre. Estas estructuras anidadas se denominan estructuras anónimas. C++ no permite estructuras anónimas.  
  
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
  
**FIN de Específicos de Microsoft**  
  

