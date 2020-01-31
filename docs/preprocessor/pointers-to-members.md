---
title: pointers_to_members (Pragma)
ms.date: 08/29/2019
f1_keywords:
- pointers_to_members_CPP
- vc-pragma.pointers_to_members
helpviewer_keywords:
- class members, pointers to
- pragmas, pointers_to_members
- members, pointers to
- pointers_to_members pragma
ms.assetid: 8325428c-c90a-4aed-9e82-cb1dda23f4ca
ms.openlocfilehash: 6058e3e4855eb745a01410e31eb9f454ef131ab1
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821413"
---
# <a name="pointers_to_members-pragma"></a>pointers_to_members (Pragma)

**C++Cuestión**

Especifica si un puntero a un miembro de clase se puede declarar antes de su definición de clase asociada. Se usa para controlar el tamaño del puntero y el código necesario para interpretar el puntero.

## <a name="syntax"></a>Sintaxis

> **#pragma pointers_to_members (** *Pointer-declaration* [ **,** *la mayoría-general-* Representation])

## <a name="remarks"></a>Notas

Puede colocar una **pointers_to_members** pragma en el archivo de código fuente como alternativa al uso de las opciones del compilador [/VMB o/VMG](../build/reference/vmb-vmg-representation-method.md) o las [palabras clave de herencia](../cpp/inheritance-keywords.md).

El argumento *Pointer-declaration* especifica si ha declarado un puntero a un miembro antes o después de la definición de función asociada. El argumento *de declaración de puntero* es uno de los dos símbolos siguientes:

| Argument | Comentarios |
|--------------|--------------|
| **full_generality** | Genera código seguro, a veces no optimo. Use **full_generality** si cualquier puntero a un miembro se declara antes de la definición de clase asociada. Este argumento siempre usa la representación de puntero especificada por el argumento de *representación más general* . Equivalente a /vmg. |
| **best_case** | Genera código seguro y óptimo que usa la representación best-case para todos los punteros a miembros. Requiere que se defina la clase antes de declarar un puntero a un miembro de la clase. El valor predeterminado es **best_case**. |

El argumento de *representación más general* especifica la representación de puntero más pequeña que el compilador puede usar de forma segura para hacer referencia a cualquier puntero a un miembro de una clase en una unidad de traducción. El argumento puede ser uno de estos valores:

| Argument | Comentarios |
|--------------|--------------|
| **single_inheritance** | La representación más general es single-inheritance, puntero a una función miembro. Produce un error si el modelo de herencia de una definición de clase para la que se declara un puntero a un miembro es múltiple o virtual. |
| **multiple_inheritance** | La representación más general es multiple-inheritance, puntero a una función miembro. Produce un error si el modelo de herencia de una definición de clase para la que se declara un puntero a un miembro es virtual. |
| **virtual_inheritance** | La representación más general es virtual-inheritance, puntero a una función miembro. Nunca produce un error. **virtual_inheritance** es el argumento predeterminado cuando se utiliza `#pragma pointers_to_members(full_generality)`. |

> [!CAUTION]
> Le recomendamos que coloque el **pointers_to_members** pragma solo en el archivo de código fuente al que desee afectar y solo después de cualquier directiva de `#include`. Esta práctica reduce el riesgo de que la Directiva pragma afecte a otros archivos y que se especifiquen accidentalmente varias definiciones para la misma variable, función o nombre de clase.

## <a name="example"></a>Ejemplo

```cpp
//   Specify single-inheritance only
#pragma pointers_to_members( full_generality, single_inheritance )
```

**Específico C++ de finalización**

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
