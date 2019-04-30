---
title: __alignof (Operador)
ms.date: 12/17/2018
f1_keywords:
- alignas_cpp
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
ms.openlocfilehash: 96c85db83c133af6f1712baa8597ed3360277854
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258257"
---
# <a name="alignof-operator"></a>__alignof (Operador)

C ++ 11 incluye el **alignof** operador que devuelve la alineación, en bytes, del tipo especificado. Para la máxima portabilidad, use el operador alignof en lugar del operador __alignof específico de Microsoft.

**Específicos de Microsoft**

Devuelve un valor de tipo `size_t` que es el requisito de alineación del tipo.

## <a name="syntax"></a>Sintaxis

```cpp
  __alignof( type )
```

## <a name="remarks"></a>Comentarios

Por ejemplo:

|Expresión|Valor|
|----------------|-----------|
|**__alignof( char )**|1|
|**__alignof( short )**|2|
|**__alignof( int )**|4|
|**__alignof( \__int64 )**|8|
|**__alignof( float )**|4|
|**__alignof( double )**|8|
|**__alignof( char\* )**|4|

El **__alignof** valor es igual que el valor de `sizeof` para los tipos básicos. Considere, no obstante, este ejemplo:

```cpp
typedef struct { int a; double b; } S;
// __alignof(S) == 8
```

En este caso, el **__alignof** valor es el requisito de alineación del elemento más grande en la estructura.

De igual forma, para

```cpp
typedef __declspec(align(32)) struct { int a; } S;
```

`__alignof(S)` es igual a `32`.

Uno de los usos de **__alignof** sería como parámetro a uno de sus propias rutinas de asignación de memoria. Por ejemplo, dada la siguiente estructura definida `S`, podría llamar a una rutina de asignación de memoria denominada `aligned_malloc` para asignar memoria en un límite de alineación determinado.

```cpp
typedef __declspec(align(32)) struct { int a; double b; } S;
int n = 50; // array size
S* p = (S*)aligned_malloc(n * sizeof(S), __alignof(S));
```

Para ofrecer compatibilidad con versiones anteriores, **_alignof** es un sinónimo de **__alignof** a menos que la opción de compilador [/Za \(deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md) es especificado.

Para obtener más información sobre la modificación de la alineación, vea:

- [pack](../preprocessor/pack.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [/Zp (Alineación de miembros de estructura)](../build/reference/zp-struct-member-alignment.md)

- [Ejemplos de alineación de estructuras](../build/x64-software-conventions.md#examples-of-structure-alignment) (x64 específico)

Para obtener más información sobre las diferencias de la alineación en código para x86 y x64, vea:

- [Conflictos con el compilador de x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)