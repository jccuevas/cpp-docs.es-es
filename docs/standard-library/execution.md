---
title: '&lt;Ejecución&gt;'
ms.date: 04/18/2019
f1_keywords:
- <execution>
- std::<execution>
helpviewer_keywords:
- execution header
ms.openlocfilehash: 3bce34019f9ed4880d72a9d16c3c8b78dde0e0e3
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268427"
---
# <a name="ltexecutiongt"></a>&lt;Ejecución&gt;

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
|[is_execution_policy Struct](is-execution-policy-struct.md)|Detecta las directivas de ejecución con el fin de excluir las firmas de función de la participación de resolución de sobrecarga ambigua en caso contrario.|
|[Clase parallel_policy](parallel-policy-class.md)|Se utiliza como un tipo único para eliminar la ambigüedad de sobrecarga del algoritmo en paralelo e indicar que se puede paralelizar la ejecución de un algoritmo paralelo.|
|[Clase parallel_unsequenced_policy](parallel-unsequenced-policy-class.md)|Se utiliza como un tipo único para eliminar la ambigüedad de sobrecarga del algoritmo en paralelo e indicar que la ejecución de un algoritmo paralelo se puede ejecutar en paralelo y vectorizada.|
|[Clase sequenced_policy](sequenced-policy-class.md)|Se utiliza como un tipo único para eliminar la ambigüedad de sobrecarga del algoritmo en paralelo y requieren que no se puede paralelizar la ejecución de un algoritmo paralelo.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<ejecución >

**Espacio de nombres:** stdext

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](cpp-standard-library-reference.md)
