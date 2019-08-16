---
title: '&lt;iomanip&gt;'
ms.date: 11/04/2016
f1_keywords:
- iomanip/std::<iomanip>
- <iomanip>
helpviewer_keywords:
- iomanip header
ms.assetid: 3681c346-4763-4037-bba4-cf0dc3447974
ms.openlocfilehash: b9da0de64bbb0ef48a6a9741ff941e6abda0e705
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449204"
---
# <a name="ltiomanipgt"></a>&lt;iomanip&gt;

Incluya el `iostreams` encabezado \<estándar iomanip > para definir varios manipuladores que toman cada uno de ellos un solo argumento.

## <a name="syntax"></a>Sintaxis

```cpp
#include <iomanip>
```

## <a name="remarks"></a>Comentarios

Cada uno de estos manipuladores devuelve un tipo sin especificar, `T1` llamado `T10`a través de, que sobrecarga `basic_istream`los \<operadores **Elem**, **TR**>`::`[> >](../standard-library/istream-operators.md#op_gt_gt) y [](../standard-library/ostream-operators.md#op_lt_lt) > < Del operador Elem,TR`::`<. `basic_ostream` \<

### <a name="manipulators"></a>Manipuladores

|||
|-|-|
|[get_money](../standard-library/iomanip-functions.md#iomanip_get_money)|Obtiene un importe monetario, opcionalmente en formato internacional.|
|[get_time](../standard-library/iomanip-functions.md#iomanip_get_time)|Obtiene una hora en una estructura de hora con un formato especificado.|
|[put_money](../standard-library/iomanip-functions.md#iomanip_put_money)|Proporciona un importe monetario, opcionalmente en formato internacional.|
|[put_time](../standard-library/iomanip-functions.md#iomanip_put_time)|Proporciona una hora en una estructura de hora y una cadena de formato que se va a usar.|
|[quoted](../standard-library/iomanip-functions.md#quoted)|Permite realizar un práctico recorrido de ida y vuelta de cadenas con operadores de inserción y extracción.|
|[resetiosflags](../standard-library/iomanip-functions.md#resetiosflags)|Borra las marcas especificadas.|
|[setbase](../standard-library/iomanip-functions.md#setbase)|Establece la base de los enteros.|
|[setfill](../standard-library/iomanip-functions.md#setfill)|Establece el carácter que se usará para rellenar los espacios en una presentación justificada a la derecha.|
|[setiosflags](../standard-library/iomanip-functions.md#setiosflags)|Establece las marcas especificadas.|
|[setprecision](../standard-library/iomanip-functions.md#setprecision)|Establece la precisión de los valores de punto flotante.|
|[setw](../standard-library/iomanip-functions.md#setw)|Especifica el ancho del campo de presentación.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programación con iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)
