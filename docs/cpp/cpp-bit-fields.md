---
title: Campos de bits de C++
ms.date: 11/19/2018
helpviewer_keywords:
- bitfields [C++]
- fields [C++], bit
- bit fields
ms.assetid: 6f4b62e3-cc1d-4e5d-bf34-05904104f71a
ms.openlocfilehash: 747920378472cc091928a080e303a0543e287aaa
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175098"
---
# <a name="c-bit-fields"></a>Campos de bits de C++

Las clases y estructuras pueden contener miembros que ocupan menos almacenamiento que un tipo entero. Estos miembros se especifican como campos de bits. La sintaxis de campo de bits *declarador de miembro* especificación se indica a continuación:

## <a name="syntax"></a>Sintaxis

*declarador* **:** *expresión constante*

## <a name="remarks"></a>Comentarios

(Opcional) *declarador* es el nombre por el que se obtiene acceso al miembro en el programa. Debe ser de tipo entero (incluidos los tipos enumerados). El *expresión-constante* especifica el número de bits que ocupa el miembro de la estructura. Se pueden utilizar campos de bits anónimos (es decir, miembros de campos de bits sin identificador) para rellenar.

> [!NOTE]
> Un campo de bits sin nombre de ancho 0 fuerza la alineación del campo de bits siguiente a la siguiente **tipo** límite, donde **tipo** es el tipo del miembro.

En el ejemplo siguiente se declara una estructura que contiene campos de bits:

```cpp
// bit_fields1.cpp
// compile with: /LD
struct Date {
   unsigned short nWeekDay  : 3;    // 0..7   (3 bits)
   unsigned short nMonthDay : 6;    // 0..31  (6 bits)
   unsigned short nMonth    : 5;    // 0..12  (5 bits)
   unsigned short nYear     : 8;    // 0..100 (8 bits)
};
```

En la ilustración siguiente se muestra el diseño de memoria conceptual de un objeto de tipo `Date`.

![Diseño de memoria de un objeto de fecha](../cpp/media/vc38uq1.png "diseño de memoria de un objeto de fecha") <br/>
Diseño de memoria de objeto de fecha

Tenga en cuenta que `nYear` tiene una longitud de 8 bits y que desbordaría el límite de palabras del tipo declarado, **sin signo** **corto**. Por lo tanto, comienza al principio de un nuevo **sin signo** **corto**. No es necesario que todos los campos de bits quepan en un objeto del tipo subyacente; se asignan nuevas unidades de almacenamiento según el número de bits solicitados en la declaración.

**Específicos de Microsoft**

El orden de los datos declarados como campos de bits es de bit bajo a bit alto, como se muestra en la ilustración anterior.

**FIN de Específicos de Microsoft**

Si la declaración de una estructura incluye un campo sin nombre de longitud 0, como se muestra en el ejemplo siguiente,

```cpp
// bit_fields2.cpp
// compile with: /LD
struct Date {
   unsigned nWeekDay  : 3;    // 0..7   (3 bits)
   unsigned nMonthDay : 6;    // 0..31  (6 bits)
   unsigned           : 0;    // Force alignment to next boundary.
   unsigned nMonth    : 5;    // 0..12  (5 bits)
   unsigned nYear     : 8;    // 0..100 (8 bits)
};
```

a continuación, el diseño de memoria es como se muestra en la ilustración siguiente:

![Diseño de objeto de fecha con cero&#45;campo de bits de longitud](../cpp/media/vc38uq2.png "objeto de diseño de fecha con cero&#45;campo de bits de longitud") <br/>
Diseño de objeto de fecha con campo de bits de longitud cero

El tipo subyacente de un campo de bits debe ser un tipo entero, como se describe en [tipos fundamentales](../cpp/fundamental-types-cpp.md).

Si el inicializador para una referencia de tipo `const T&` es un valor l que hace referencia a un campo de bits de tipo `T`, la referencia no está enlazada directamente en el campo de bits. En su lugar, la referencia se enlaza a un archivo temporal que se inicializa para contener el valor del campo de bits.

## <a name="restrictions-on-bit-fields"></a>Restricciones de los campos de bits

En la lista siguiente se detallan operaciones erróneas en campos de bits:

- Tomar la dirección de un campo de bits.

- Inicializando no**const** referencia con un campo de bits.

## <a name="see-also"></a>Vea también

[Clases y structs](../cpp/classes-and-structs-cpp.md)