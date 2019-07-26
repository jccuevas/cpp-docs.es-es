---
title: forward_iterator_tag (Struct)
ms.date: 11/04/2016
f1_keywords:
- xutility/std::forward_iterator_tag
helpviewer_keywords:
- forward_iterator_tag struct
- forward_iterator_tag class
ms.assetid: 68b633ac-b135-4e9e-837d-14248a262ec5
ms.openlocfilehash: 687e39ce752bc0d4d289421887570dea6870f8f3
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457120"
---
# <a name="forwarditeratortag-struct"></a>forward_iterator_tag (Struct)

Clase que proporciona un tipo de valor devuelto para una función **iterator_category** que representa un iterador hacia delante.

## <a name="syntax"></a>Sintaxis

```cpp
struct forward_iterator_tag    : public input_iterator_tag {};
```

## <a name="remarks"></a>Comentarios

Las clases de etiquetas de categoría se usan como etiquetas de compilación para la selección de algoritmos. La función de plantilla debe descubrir cuál es la categoría más específica de su argumento de iterador para que pueda usar el algoritmo más eficaz en tiempo de compilación. Para cada iterador de tipo `Iterator`, `iterator_traits`< `Iterator`>  **::iterator_category** debe definirse para que sea la etiqueta de categoría más específica que describa el comportamiento del iterador.

El tipo es igual a **iterator**\< **Iter**>  **::iterator_category** cuando **Iter** describe un objeto que puede actuar como un iterador hacia delante.

## <a name="example"></a>Ejemplo

Vea [iterator_traits](../standard-library/iterator-traits-struct.md) o [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) para obtener un ejemplo de cómo usar **iterator_tag**s.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<iterator>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[input_iterator_tag (Struct)](../standard-library/input-iterator-tag-struct.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
