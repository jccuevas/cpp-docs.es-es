---
title: input_iterator_tag (Struct)
ms.date: 11/04/2016
f1_keywords:
- xutility/std::input_iterator_tag
helpviewer_keywords:
- input_iterator_tag class
- input_iterator_tag struct
ms.assetid: ad68a4c6-f315-4ce1-8b74-c1fc71bd1577
ms.openlocfilehash: 5478a8f9fa6013202a1ea8dd838eedb80b9c367e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159256"
---
# <a name="inputiteratortag-struct"></a>input_iterator_tag (Struct)

Una clase que proporciona un tipo de valor devuelto para `iterator_category` función que representa un iterador de entrada.

## <a name="syntax"></a>Sintaxis

input_iterator_tag (struct) {};

## <a name="remarks"></a>Comentarios

Las clases de etiquetas de categoría se usan como etiquetas de compilación para la selección de algoritmos. La función de plantilla debe buscar la categoría más específica de su argumento de iterador para que pueda usar el algoritmo más eficaz en tiempo de compilación. Para cada iterador de tipo `Iterator`, `iterator_traits`< `Iterator`> **::iterator_category** debe definirse para que sea la etiqueta de categoría más específica que describa el comportamiento del iterador.

El tipo es igual a **iterador** \< **Iter**> **:: iterator_category** cuando `Iter` describe un objeto que puede actuar como un iterador de entrada.

## <a name="example"></a>Ejemplo

Consulte [iterator_traits](../standard-library/iterator-traits-struct.md) o [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) para obtener un ejemplo de cómo usar `iterator_tag`s.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<iterator>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
