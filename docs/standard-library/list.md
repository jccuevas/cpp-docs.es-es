---
title: '&lt;lista&gt;'
ms.date: 11/04/2016
f1_keywords:
- <list>
- std::<list>
helpviewer_keywords:
- list header
ms.assetid: 2345823b-5612-44d8-95d3-aa96ed076d17
ms.openlocfilehash: 8eb497e6a4380affd0f13f41c7b55990c562b7d3
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453654"
---
# <a name="ltlistgt"></a>&lt;lista&gt;

Define la lista de clases de plantilla de contenedores y varias plantillas auxiliares.

## <a name="syntax"></a>Sintaxis

```cpp
#include <list>
```

> [!NOTE]
> La \<biblioteca de > de listas también `#include <initializer_list>` utiliza la instrucción.

## <a name="members"></a>Miembros

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator!=](../standard-library/list-operators.md#op_neq)|Comprueba si el objeto de lista del lado izquierdo del operador no es igual que el objeto de lista del lado derecho.|
|[operator<](../standard-library/list-operators.md#op_lt)|Comprueba si el objeto de lista del lado izquierdo del operador es menor que el objeto de lista del lado derecho.|
|[operator\<=](../standard-library/list-operators.md#op_gt_eq)|Comprueba si el objeto de lista del lado izquierdo del operador es menor o igual que el objeto de lista del lado derecho.|
|[operator==](../standard-library/list-operators.md#op_eq_eq)|Comprueba si el objeto de lista del lado izquierdo del operador es igual que el objeto de lista del lado derecho.|
|[operator>](../standard-library/list-operators.md#op_gt)|Comprueba si el objeto de lista del lado izquierdo del operador es mayor que el objeto de lista del lado derecho.|
|[operator>=](../standard-library/list-operators.md#op_gt_eq)|Comprueba si el objeto de lista del lado izquierdo del operador es mayor o igual que el objeto de lista del lado derecho.|

### <a name="functions"></a>Funciones

|||
|-|-|
|[swap](../standard-library/list-functions.md#swap)|Intercambia los elementos de dos listas.|

### <a name="classes"></a>Clases

|||
|-|-|
|[Clase list](../standard-library/list-class.md)|Una clase de plantilla de contenedores de secuencias que mantienen sus elementos en disposición lineal y permiten realizar inserciones y eliminaciones de manera eficiente en cualquier ubicación de la secuencia.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
