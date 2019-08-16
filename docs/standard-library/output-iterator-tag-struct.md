---
title: output_iterator_tag (Struct)
ms.date: 11/04/2016
f1_keywords:
- xutility/std::output_iterator_tag
helpviewer_keywords:
- output_iterator_tag class
- output_iterator_tag struct
ms.assetid: c23a4331-b069-4fa0-9c3a-1c9be7095553
ms.openlocfilehash: 942e2214f42f97e262d4daf7836e8b6ced0e0ab2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453018"
---
# <a name="outputiteratortag-struct"></a>output_iterator_tag (Struct)

Una clase que proporciona un tipo de valor `iterator_category` devuelto para la función que representa un iterador de salida.

## <a name="syntax"></a>Sintaxis

struct output_iterator_tag {};

## <a name="remarks"></a>Comentarios

Las clases de etiquetas de categoría se usan como etiquetas de compilación para la selección de algoritmos. La función de plantilla debe buscar la categoría más específica de su argumento de iterador para que pueda usar el algoritmo más eficaz en tiempo de compilación. Para cada iterador de tipo `Iterator`, `iterator_traits`< `Iterator`>  **::iterator_category** debe definirse para que sea la etiqueta de categoría más específica que describa el comportamiento del iterador.

El tipo es el mismo que  \< el iterador **ITER**>  **:: iterator_category** cuando `Iter` describe un objeto que puede actuar como un iterador de salida.

Esta etiqueta no está parametrizada en `value_type` o `difference_type` para el iterador, como con las demás etiquetas de iterador, porque los iteradores de salida no tienen `value_type` ni `difference_type`.

## <a name="example"></a>Ejemplo

Vea [iterator_traits](../standard-library/iterator-traits-struct.md) o [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) para obtener un ejemplo de cómo usar `iterator_tag`s.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<iterator>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
