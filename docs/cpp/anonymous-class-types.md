---
title: Tipos de clase anónima
ms.date: 11/04/2016
helpviewer_keywords:
- class types [C++], anonymous
- anonymous class types
ms.assetid: 9ba667b2-8c2a-4c29-82a6-fa120b9233c8
ms.openlocfilehash: 815cc4a81addc673349a3133b24ed73cfe0207e2
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857676"
---
# <a name="anonymous-class-types"></a>Tipos de clase anónima

Las clases pueden ser anónimas, es decir, se pueden declarar sin un *identificador*. Esto resulta útil cuando se reemplaza un nombre de clase por un nombre de **typedef** , como en el siguiente procedimiento:

```cpp
typedef struct
{
    unsigned x;
    unsigned y;
} POINT;
```

> [!NOTE]
>  El uso de las clases anónimas que se muestra en el ejemplo anterior es útil para mantener la compatibilidad con el código de C existente. En algunos código de C, el uso de **typedef** junto con estructuras anónimas es frecuente.

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

En el código anterior, se puede tener acceso a `iValue` mediante el operador de selección de miembro de objeto ( **.** ) de la siguiente manera:

```cpp
int i = ptv.iValue;
```

Las clases anónimas están sujetas a determinadas restricciones. (Para obtener más información sobre las uniones anónimas, vea [uniones](../cpp/unions.md)). Clases anónimas:

- No pueden tener un constructor o un destructor.

- No se pueden pasar como argumentos a funciones (a menos que la comprobación de tipos se rechace mediante el uso de puntos suspensivos).

- No se pueden devolver como valores devueltos de funciones.

## <a name="anonymous-structs"></a>Structs anónimos

**Específicos de Microsoft**

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
