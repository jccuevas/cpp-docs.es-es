---
title: '&lt;&gt; de ejecución'
ms.date: 04/18/2019
f1_keywords:
- <execution>
- std::<execution>
helpviewer_keywords:
- execution header
ms.openlocfilehash: 81e9aa63265c367412fda709aacd5ca3953e9fdf
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445032"
---
# <a name="ltexecutiongt"></a>&lt;&gt; de ejecución

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
|[is_execution_policy struct](is-execution-policy-struct.md)|Detecta las directivas de ejecución con el fin de excluir las firmas de función de la participación de resolución de sobrecarga ambigua de otro modo.|
|[parallel_policy (clase)](parallel-policy-class.md)|Se usa como un tipo único para eliminar la ambigüedad de sobrecarga de algoritmos paralelos e indicar que la ejecución de un algoritmo paralelo puede ejecutarse en paralelo.|
|[parallel_unsequenced_policy (clase)](parallel-unsequenced-policy-class.md)|Se usa como un tipo único para eliminar la ambigüedad de sobrecarga de algoritmos paralelos e indicar que la ejecución de un algoritmo paralelo se puede paralelizar y vectorizar.|
|[sequenced_policy (clase)](sequenced-policy-class.md)|Se usa como un tipo único para eliminar la ambigüedad de la sobrecarga del algoritmo paralelo y requerir que la ejecución de un algoritmo paralelo no se ejecute en paralelo.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<> de ejecución

**Espacio de nombres:** stdext

## <a name="see-also"></a>Consulte también

[Referencia de archivos de encabezado](cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](thread-safety-in-the-cpp-standard-library.md)\
[Referencia de biblioteca estándar de C++](cpp-standard-library-reference.md)
