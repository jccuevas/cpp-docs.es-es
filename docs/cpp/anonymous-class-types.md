---
title: Tipos de clase anónima | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- class types [C++], anonymous
- anonymous class types
ms.assetid: 9ba667b2-8c2a-4c29-82a6-fa120b9233c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8890a128ff625ead27ef34be6d057e879b22a5f6
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402739"
---
# <a name="anonymous-class-types"></a>Tipos de clase anónima
Las clases pueden ser anónimas, es decir, se pueden declarar sin un *identificador*. Esto es útil cuando se reemplaza un nombre de clase con un **typedef** nombre, como en el siguiente ejemplo:  
  
```cpp 
typedef struct  
{  
    unsigned x;  
    unsigned y;  
} POINT;  
```  
  
> [!NOTE]
>  El uso de las clases anónimas que se muestra en el ejemplo anterior es útil para mantener la compatibilidad con el código de C existente. En algún código de C, el uso de **typedef** junto con estructuras anónimas es frecuente.  
  
 Las clases anónimas también son útiles cuando se desea que una referencia a un miembro de clase aparezca como si no estuviera contenida en una clase independiente, como en el siguiente ejemplo de código:  
  
```cpp 
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
  
 En el código anterior, `iValue` se puede acceder mediante el operador de selección de miembro de objeto (**.**) como sigue:  
  
```cpp 
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
  
```cpp 
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