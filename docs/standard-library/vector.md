---
title: '&lt;vector&gt;'
ms.date: 11/04/2016
f1_keywords:
- <vector>
helpviewer_keywords:
- vector header
ms.assetid: c1431ad8-c0b6-4dbb-89c4-5f651e432d7f
ms.openlocfilehash: 19068de41cfdcb17ae624858c137bf624851479f
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72684065"
---
# <a name="ltvectorgt"></a>&lt;vector&gt;

Define el vector de plantilla de la clase de contenedor y varias plantillas auxiliares.

El `vector` es un contenedor que organiza los elementos de un tipo determinado en una secuencia lineal. Permite el acceso aleatorio rápido a cualquier elemento, así como agregar y eliminar elementos de la secuencia de forma dinámica. El `vector` es el contenedor más apropiado para una secuencia cuando el rendimiento de acceso aleatorio es importante.

> [!NOTE]
> La biblioteca de > de \<vector también utiliza la instrucción `#include <initializer_list>`.

Para más información sobre la clase `vector`, vea [vector (Clase)](../standard-library/vector-class.md). Para más información sobre la especialización `vector<bool>`, vea [vector\<bool> (Clase)](../standard-library/vector-bool-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
namespace std {
template <class Type, class Allocator>
class vector;
template <class Allocator>
class vector<bool>;

template <class Allocator>
struct hash<vector<bool, Allocator>>;

// TEMPLATE FUNCTIONS
template <class Type, class Allocator>
bool operator== (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator!= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator<(
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator> (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator<= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator>= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
void swap (
    vector<Type, Allocator>& left,
    vector<Type, Allocator>& right);

}  // namespace std
```

### <a name="parameters"></a>Parámetros

*Escribir* \
Parámetro de plantilla para el tipo de datos almacenados en el vector.

@No__t_1 de *asignador*
Parámetro de plantilla para el objeto de asignador almacenado responsable de la asignación y desasignación de memoria.

\ *izquierda*
Primer vector (izquierdo) en una operación de comparación

\ *derecha*
Segundo vector (derecho) en una operación de comparación.

## <a name="members"></a>Miembros

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator! =](../standard-library/vector-operators.md#op_neq)|Comprueba si el objeto de vector en el lado izquierdo del operador no es igual que el objeto de vector en el lado derecho.|
|[operator<](../standard-library/vector-operators.md#op_lt)|Comprueba si el objeto de vector en el lado izquierdo del operador es menor que el objeto de vector en el lado derecho.|
|[operator\<=](../standard-library/vector-operators.md#op_gt_eq)|Comprueba si el objeto de vector en el lado izquierdo del operador es menor o igual que el objeto de vector en el lado derecho.|
|[operator==](../standard-library/vector-operators.md#op_eq_eq)|Comprueba si el objeto de vector en el lado izquierdo del operador es igual que el objeto de vector en el lado derecho.|
|[operator>](../standard-library/vector-operators.md#op_gt)|Comprueba si el objeto de vector en el lado izquierdo del operador es mayor que el objeto de vector en el lado derecho|
|[operator>=](../standard-library/vector-operators.md#op_gt_eq)|Comprueba si el objeto de vector en el lado izquierdo del operador es mayor o igual que el objeto de vector en el lado derecho|

### <a name="classes"></a>Clases

|||
|-|-|
|[vector (Clase)](../standard-library/vector-class.md)|Una plantilla de clase de contenedores de secuencias que organiza los elementos de un tipo determinado en una organización lineal y permite el acceso aleatorio rápido a cualquier elemento.|

### <a name="specializations"></a>Especializaciones

|||
|-|-|
|hash|Devuelve un hash del vector.|
|[vector\<bool> (Clase)](../standard-library/vector-bool-class.md)|Una especialización completa del vector de la plantilla de clase para los elementos de tipo `bool` con un asignador para el tipo subyacente utilizado por la especialización.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<vector>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
