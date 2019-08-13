---
title: '&lt;vector&gt;'
ms.date: 11/04/2016
f1_keywords:
- <vector>
helpviewer_keywords:
- vector header
ms.assetid: c1431ad8-c0b6-4dbb-89c4-5f651e432d7f
ms.openlocfilehash: 59424a9f6a9434b5d7d3f4298cbb0bc03926621c
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957064"
---
# <a name="ltvectorgt"></a>&lt;vector&gt;

Define el vector de clases de plantilla de contenedores y varias plantillas auxiliares.

El `vector` es un contenedor que organiza los elementos de un tipo determinado en una secuencia lineal. Permite el acceso aleatorio rápido a cualquier elemento, así como agregar y eliminar elementos de la secuencia de forma dinámica. El `vector` es el contenedor más apropiado para una secuencia cuando el rendimiento de acceso aleatorio es importante.

> [!NOTE]
> La \<biblioteca de > vectoriales también `#include <initializer_list>` utiliza la instrucción.

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

*Automáticamente*\
Parámetro de plantilla para el tipo de datos almacenados en el vector.

*Asignador*\
Parámetro de plantilla para el objeto de asignador almacenado responsable de la asignación y desasignación de memoria.

*salido*\
Primer vector (izquierdo) en una operación de comparación

*correcta*\
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
|[vector (Clase)](../standard-library/vector-class.md)|Una clase de plantilla de contenedores de secuencias que organiza los elementos de un tipo determinado en una organización lineal y permite el acceso aleatorio rápido a cualquier elemento.|

### <a name="specializations"></a>Especializaciones

|||
|-|-|
|hash|Devuelve un hash del vector.|
|[vector\<bool> (Clase)](../standard-library/vector-bool-class.md)|Una especialización completa de la clase de plantilla vector para los elementos del tipo `bool` con un asignador para el tipo subyacente utilizado por la especialización.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<vector>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
