---
title: '&lt;remota&gt;'
ms.date: 04/18/2019
f1_keywords:
- <execution>
- std::<execution>
helpviewer_keywords:
- execution header
ms.openlocfilehash: 3b0ccd540c56500c2f265aa6192a12fc2d5078b0
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457971"
---
# <a name="ltexecutiongt"></a>&lt;remota&gt;

Describe las directivas de ejecución para los algoritmos paralelos.

## <a name="syntax"></a>Sintaxis

```
namespace std {
    template<class T> inline constexpr bool is_execution_policy_v = is_execution_policy<T>::value;
}
namespace std::execution {
    inline constexpr sequenced_policy seq { unspecified };
    inline constexpr parallel_policy par { unspecified };
    inline constexpr parallel_unsequenced_policy par_unseq { unspecified };
}
```
### <a name="classes-and-structs"></a>Clases y structs

|||
|-|-|
|[Struct is_execution_policy](is-execution-policy-struct.md)|Detecta las directivas de ejecución con el fin de excluir las firmas de función de la participación de resolución de sobrecarga ambigua de otro modo.|
|[Clase parallel_policy](parallel-policy-class.md)|Se usa como un tipo único para eliminar la ambigüedad de sobrecarga de algoritmos paralelos e indicar que la ejecución de un algoritmo paralelo puede ejecutarse en paralelo.|
|[Clase parallel_unsequenced_policy](parallel-unsequenced-policy-class.md)|Se usa como un tipo único para eliminar la ambigüedad de sobrecarga de algoritmos paralelos e indicar que la ejecución de un algoritmo paralelo se puede paralelizar y vectorizar.|
|[Clase sequenced_policy](sequenced-policy-class.md)|Se usa como un tipo único para eliminar la ambigüedad de la sobrecarga del algoritmo paralelo y requerir que la ejecución de un algoritmo paralelo no se ejecute en paralelo.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<> de ejecución

**Espacio de nombres:** stdext

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](thread-safety-in-the-cpp-standard-library.md)\
[Referencia de biblioteca estándar de C++](cpp-standard-library-reference.md)
