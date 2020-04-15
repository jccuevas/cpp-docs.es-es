---
title: Tipos de clase anónima
ms.date: 11/04/2016
helpviewer_keywords:
- class types [C++], anonymous
- anonymous class types
ms.assetid: 9ba667b2-8c2a-4c29-82a6-fa120b9233c8
ms.openlocfilehash: 611c1ed9853fc7e6e0788a7276890b14ec84a523
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373349"
---
# <a name="anonymous-class-types"></a>Tipos de clase anónima

Las clases pueden ser anónimas, es decir, se pueden declarar sin un *identificador.* Esto resulta útil cuando se reemplaza un nombre de clase por un nombre **typedef,** como se muestra a continuación:

```cpp
typedef struct
{
    unsigned x;
    unsigned y;
} POINT;
```

> [!NOTE]
> El uso de las clases anónimas que se muestra en el ejemplo anterior es útil para mantener la compatibilidad con el código de C existente. En algunos códigos C, prevalece el uso de **typedef** junto con estructuras anónimas.

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

En el código `iValue` anterior, se puede acceder a ellos mediante el operador de selección de miembros del objeto (**.**) de la siguiente manera:

```cpp
int i = ptv.iValue;
```

Las clases anónimas están sujetas a determinadas restricciones. (Para obtener más información acerca de las uniones anónimas, consulte [Uniones](../cpp/unions.md).) Clases anónimas:

- No pueden tener un constructor o un destructor.

- No se pueden pasar como argumentos a funciones (a menos que la comprobación de tipos se rechace mediante el uso de puntos suspensivos).

- No se pueden devolver como valores devueltos de funciones.

## <a name="anonymous-structs"></a>Structs anónimos

**Microsoft Specific**

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

**END Microsoft Specific**
