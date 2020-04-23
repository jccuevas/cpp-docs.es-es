---
title: Tipos de clase anónima
ms.date: 11/04/2016
helpviewer_keywords:
- class types [C++], anonymous
- anonymous class types
ms.assetid: 9ba667b2-8c2a-4c29-82a6-fa120b9233c8
ms.openlocfilehash: e227f48588c3c4f59c0d0bd28ab16178de159b58
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032088"
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

- No se puede pasar como argumentos a las funciones (a menos que la comprobación de tipos se derrote mediante puntos suspensivos).

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
