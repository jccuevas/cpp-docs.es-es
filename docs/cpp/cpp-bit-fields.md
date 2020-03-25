---
title: Campos de bits de C
ms.date: 11/19/2018
helpviewer_keywords:
- bitfields [C++]
- fields [C++], bit
- bit fields
ms.assetid: 6f4b62e3-cc1d-4e5d-bf34-05904104f71a
ms.openlocfilehash: b952ca0aab5c4417f22fd958514894c53a39f800
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170610"
---
# <a name="c-bit-fields"></a>Campos de bits de C

Las clases y estructuras pueden contener miembros que ocupan menos almacenamiento que un tipo entero. Estos miembros se especifican como campos de bits. La sintaxis de la especificación de *declarador de miembro* de campo de bits es la siguiente:

## <a name="syntax"></a>Sintaxis

*declarator* **:** *Constant-Expression*

## <a name="remarks"></a>Observaciones

El *declarador* (opcional) es el nombre por el que se tiene acceso al miembro en el programa. Debe ser de tipo entero (incluidos los tipos enumerados). *Constant-Expression* especifica el número de bits que el miembro ocupa en la estructura. Se pueden utilizar campos de bits anónimos (es decir, miembros de campos de bits sin identificador) para rellenar.

> [!NOTE]
> Un campo de bits sin nombre de width 0 fuerza la alineación del campo de bits siguiente al siguiente límite de **tipo** , donde **Type** es el tipo del miembro.

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

![Diseño de memoria de un objeto de fecha](../cpp/media/vc38uq1.png "Diseño de memoria de un objeto de fecha") <br/>
Diseño de memoria de objeto de fecha

Tenga en cuenta que `nYear` tiene una longitud de 8 bits y desbordaría el límite de palabras del tipo declarado, **unsigned** **Short**. Por lo tanto, se inicia al principio de un nuevo **unsigned** **Short**. No es necesario que todos los campos de bits quepan en un objeto del tipo subyacente; se asignan nuevas unidades de almacenamiento según el número de bits solicitados en la declaración.

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

después, el diseño de memoria es como se muestra en la ilustración siguiente:

![Diseño de objeto de fecha con&#45;campo de bits de longitud cero](../cpp/media/vc38uq2.png "Diseño de objeto de fecha con&#45;campo de bits de longitud cero") <br/>
Diseño de objeto de fecha con campo de bits de longitud cero

El tipo subyacente de un campo de bits debe ser un tipo entero, tal y como se describe en [tipos integrados](../cpp/fundamental-types-cpp.md).

Si el inicializador de una referencia de tipo `const T&` es un valor l que hace referencia a un campo de bits de tipo `T`, la referencia no se enlaza directamente al campo de bits. En su lugar, la referencia se enlaza a una inicializada temporal para contener el valor del campo de bits.

## <a name="restrictions-on-bit-fields"></a>Restricciones de los campos de bits

En la lista siguiente se detallan operaciones erróneas en campos de bits:

- Tomar la dirección de un campo de bits.

- Inicializar una referencia no**const** con un campo de bits.

## <a name="see-also"></a>Consulte también

[Clases y structs](../cpp/classes-and-structs-cpp.md)
