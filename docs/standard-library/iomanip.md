---
title: '&lt;iomanip&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- iomanip/std::<iomanip>
- <iomanip>
dev_langs:
- C++
helpviewer_keywords:
- iomanip header
ms.assetid: 3681c346-4763-4037-bba4-cf0dc3447974
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a410dae35771d89b9d9ae72c8221501f051d10e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="ltiomanipgt"></a>&lt;iomanip&gt;

Incluir el `iostreams` encabezado estándar \<iomanip > para definir varios manipuladores que toman un solo argumento.

## <a name="syntax"></a>Sintaxis

```cpp
#include <iomanip>

```

## <a name="remarks"></a>Comentarios

Cada uno de estos manipuladores devuelve un tipo sin especificar, denominado de **T1** a **T10**, que sobrecarga `basic_istream`\<**Elem**, **Tr**>`::`[operator>>](../standard-library/istream-operators.md#op_gt_gt) y `basic_ostream`\<**Elem**, **Tr**>`::`[operator<<](../standard-library/ostream-operators.md#op_lt_lt).

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

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Programación con iostream](../standard-library/iostream-programming.md)<br/>
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)<br/>
