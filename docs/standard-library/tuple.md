---
title: '&lt;tuple&gt;'
ms.date: 11/04/2016
f1_keywords:
- <tuple>
helpviewer_keywords:
- tuple header
ms.assetid: e4ef5c2d-318b-44f6-8bce-fce4ecd796a3
ms.openlocfilehash: 2e46b3997096c6e61f7dd6140131e3f10223b8e7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399426"
---
# <a name="lttuplegt"></a>&lt;tuple&gt;

Define una `tuple` de plantilla cuyas instancias contienen objetos de tipos diferentes.

## <a name="syntax"></a>Sintaxis

```cpp
#include <tuple>
```

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[tuple](../standard-library/tuple-class.md)|Ajusta una secuencia de elementos de longitud fija.|
|[tuple_element (Clase)](../standard-library/tuple-element-class-tuple.md)|Ajusta el tipo de un elemento `tuple`.|
|[tuple_size (Clase)](../standard-library/tuple-size-class-tuple.md)|Contiene el número de elementos `tuple`.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator==](../standard-library/tuple-operators.md#op_eq_eq)|Comparación de objetos `tuple`, igualdad|
|[operator!=](../standard-library/tuple-operators.md#op_neq)|Comparación de objetos `tuple`, desigualdad|
|[operator<](../standard-library/tuple-operators.md#op_lt)|Comparación de objetos `tuple`, menor que|
|[operator<=](../standard-library/tuple-operators.md#op_lt_eq)|Comparación de objetos `tuple`, menor o igual que|
|[operator>](../standard-library/tuple-operators.md#op_gt)|Comparación de objetos `tuple`, mayor que|
|[operator>=](../standard-library/tuple-operators.md#op_gt_eq)|Comparación de objetos `tuple`, mayor o igual que|

### <a name="functions"></a>Funciones

|Función|Descripción|
|-|-|
|[get](../standard-library/tuple-functions.md#get)|Obtiene un elemento de un objeto `tuple`.|
|[make_tuple](../standard-library/tuple-functions.md#make_tuple)|Crea una `tuple` a partir de valores de elemento.|
|[tie](../standard-library/tuple-functions.md#tie)|Crea una `tuple` a partir de referencias de elemento.|

## <a name="see-also"></a>Vea también

[\<array>](../standard-library/array.md)<br/>
