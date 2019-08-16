---
title: Range (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.range
helpviewer_keywords:
- range attribute
ms.assetid: f352f79e-ecb3-4cdd-9cdd-8406ef473594
ms.openlocfilehash: d1221192eb1813d759f293fe5555d7aaa5b367ab
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514144"
---
# <a name="range-c"></a>range (C++)

Especifica un intervalo de valores permitidos para los argumentos o campos cuyos valores se establecen en tiempo de ejecución.

## <a name="syntax"></a>Sintaxis

```cpp
[ range(low, high) ]
```

### <a name="parameters"></a>Parámetros

*low*<br/>
Valor de intervalo inferior.

*high*<br/>
Valor de intervalo alto.

## <a name="remarks"></a>Comentarios

El atributo de **intervalo** C++ tiene la misma funcionalidad que el atributo MIDL de [intervalo](/windows/win32/Midl/range) .

## <a name="example"></a>Ejemplo

```cpp
// cpp_attr_ref_range.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
   HRESULT length_is1([in, range(0, 999)] long f, [in, length_is(f)] char array[10]);
   HRESULT length_is2([in, range(-99, -1)] long f, [in, length_is("f"), size_is(10)] char *array);
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Método de interfaz, parámetro de interfaz|
|**Reiterativo**|Sin|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[Atributos de parámetro](parameter-attributes.md)<br/>
[Atributos de miembros de datos](data-member-attributes.md)