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
ms.openlocfilehash: fb5b277252b6c1422a87c5f2a2e2b7230ec49632
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219061"
---
# <a name="pointers_to_members-pragma"></a>pointers_to_members (Pragma)

**C++Cuestión**

Especifica si un puntero a un miembro de clase se puede declarar antes de su definición de clase asociada. Se usa para controlar el tamaño del puntero y el código necesario para interpretar el puntero.

## <a name="syntax"></a>Sintaxis

> **#pragma pointers_to_members (** *declaración de puntero* [ **,** *más-general-* Representation])

## <a name="remarks"></a>Comentarios

Puede colocar una pragma **pointers_to_members** en el archivo de código fuente como alternativa al uso de las opciones del compilador [/VMB o/VMG](../build/reference/vmb-vmg-representation-method.md) o las [palabras clave de herencia](../cpp/inheritance-keywords.md).

El argumento *Pointer-declaration* especifica si ha declarado un puntero a un miembro antes o después de la definición de función asociada. El argumento *de declaración de puntero* es uno de los dos símbolos siguientes:

| Argumento | Comentarios |
|--------------|--------------|
| **full_generality** | Genera código seguro, a veces no optimo. Use **full_generality** si cualquier puntero a un miembro se declara antes de la definición de clase asociada. Este argumento siempre usa la representación de puntero especificada por el argumento de *representación más general* . Equivalente a /vmg. |
| **best_case** | Genera código seguro y óptimo que usa la representación best-case para todos los punteros a miembros. Requiere que se defina la clase antes de declarar un puntero a un miembro de la clase. El valor predeterminado es **best_case**. |

El argumento de *representación más general* especifica la representación de puntero más pequeña que el compilador puede usar de forma segura para hacer referencia a cualquier puntero a un miembro de una clase en una unidad de traducción. El argumento puede ser uno de estos valores:

| Argumento | Comentarios |
|--------------|--------------|
| **single_inheritance** | La representación más general es single-inheritance, puntero a una función miembro. Produce un error si el modelo de herencia de una definición de clase para la que se declara un puntero a un miembro es múltiple o virtual. |
| **multiple_inheritance** | La representación más general es multiple-inheritance, puntero a una función miembro. Produce un error si el modelo de herencia de una definición de clase para la que se declara un puntero a un miembro es virtual. |
| **virtual_inheritance** | La representación más general es virtual-inheritance, puntero a una función miembro. Nunca produce un error. **virtual_inheritance** es el argumento predeterminado cuando `#pragma pointers_to_members(full_generality)` se usa. |

> [!CAUTION]
> Le recomendamos que coloque la pragma **pointers_to_members** solo en el archivo de código fuente al que desee afectar y solo después de las `#include` directivas. Esta práctica reduce el riesgo de que la pragma afecte a otros archivos, y de que especifique accidentalmente varias definiciones para la misma variable, función o nombre de clase.

## <a name="example"></a>Ejemplo

```cpp
//   Specify single-inheritance only
#pragma pointers_to_members( full_generality, single_inheritance )
```

**Específico C++ de finalización**

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
