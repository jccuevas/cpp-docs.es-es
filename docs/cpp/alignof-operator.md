---
title: __alignof (Operador)
ms.date: 12/17/2018
f1_keywords:
- __alignof_cpp
- alignof_cpp
- __alignof
- _alignof
helpviewer_keywords:
- alignas [C++]
- alignment of structures
- __alignof keyword [C++]
- alignof [C++]
- types [C++], alignment requirements
ms.assetid: acb1eed7-6398-40bd-b0c5-684ceb64afbc
ms.openlocfilehash: 6bddce29dd97d965303a58cc72aa97dfe8cbd8d7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181543"
---
# <a name="__alignof-operator"></a>__alignof (Operador)

C++ 11 presenta el operador **Aligning** que devuelve la alineación, en bytes, del tipo especificado. Para la máxima portabilidad, use el operador alignof en lugar del operador __alignof específico de Microsoft.

**Específicos de Microsoft**

Devuelve un valor de tipo `size_t` que es el requisito de alineación del tipo.

## <a name="syntax"></a>Sintaxis

```cpp
  __alignof( type )
```

## <a name="remarks"></a>Observaciones

Por ejemplo:

|Expression|Value|
|----------------|-----------|
|**__alignof (Char)**|1|
|**__alignof (short)**|2|
|**__alignof (int)**|4|
|**__alignof (_int64 \_)**|8|
|**__alignof (float)**|4|
|**__alignof (Double)**|8|
|**__alignof (char\*)**|4|

El valor **__alignof** es el mismo que el valor de `sizeof` para los tipos básicos. Considere, no obstante, este ejemplo:

```cpp
typedef struct { int a; double b; } S;
// __alignof(S) == 8
```

En este caso, el valor de **__alignof** es el requisito de alineación del elemento más grande de la estructura.

De igual forma, para

```cpp
typedef __declspec(align(32)) struct { int a; } S;
```

`__alignof(S)` es igual a `32`.

Un uso de **__alignof** sería como parámetro de una de sus propias rutinas de asignación de memoria. Por ejemplo, dada la siguiente estructura definida `S`, podría llamar a una rutina de asignación de memoria denominada `aligned_malloc` para asignar memoria en un límite de alineación determinado.

```cpp
typedef __declspec(align(32)) struct { int a; double b; } S;
int n = 50; // array size
S* p = (S*)aligned_malloc(n * sizeof(S), __alignof(S));
```

Por compatibilidad con versiones anteriores, **_alignof** es un sinónimo de **__alignof** a menos que se especifique la opción del compilador [/za \(deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md) .

Para obtener más información sobre la modificación de la alineación, vea:

- [pack](../preprocessor/pack.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [/Zp (Alineación de miembros de estructura)](../build/reference/zp-struct-member-alignment.md)

- [Ejemplos de alineación de estructura](../build/x64-software-conventions.md#examples-of-structure-alignment) (específico de x64)

Para obtener más información sobre las diferencias de la alineación en código para x86 y x64, vea:

- [Conflictos con el compilador de x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
