---
title: support_error_info (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.support_error_info
helpviewer_keywords:
- support_error_info attribute
ms.assetid: 20a2b55c-4738-4b35-a71d-e5e9c3a7e3bc
ms.openlocfilehash: e61ef2efbdc4039f496d7ffbcccc37cc8d111935
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166151"
---
# <a name="support_error_info"></a>support_error_info

Implementa compatibilidad para devolver errores detallados.

## <a name="syntax"></a>Sintaxis

```cpp
[ support_error_info(error_interface=uuid) ]
```

### <a name="parameters"></a>Parámetros

*error_interface*<br/>
Identificador de la interfaz que implementa `IErrorInfo`.

## <a name="remarks"></a>Observaciones

El atributo de C++ **support_error_info** implementa compatibilidad para devolver al cliente errores detallados y contextuales detectados por el objeto de destino. Para que el objeto admita errores, el objeto debe implementar los métodos de la interfaz `IErrorInfo`. Para obtener más información, consulte [Compatibilidad con IDispatch e IErrorInfo](../../atl/supporting-idispatch-and-ierrorinfo.md).

Este atributo agrega la clase [ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md) como una clase base al objeto de destino. Esto produce una implementación predeterminada de `ISupportErrorInfo` y se puede usar cuando una sola interfaz genera errores en un objeto.

## <a name="example"></a>Ejemplo

El código siguiente agrega compatibilidad predeterminada con la interfaz de `ISupportErrorInfo` al objeto `CMyClass`.

```cpp
// cpp_attr_ref_support_error_info.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="mymod")];
[object, uuid("f0b17d66-dc6e-4662-baaf-76758e09c878")]
__interface IMyErrors
{
};

[ coclass, support_error_info("IMyErrors"),
  uuid("854dd392-bdc7-4781-8667-8757936f2a4f") ]
class CMyClass
{
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**class**|
|**Reiterativo**|Sí|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos COM](com-attributes.md)<br/>
[Atributos de clase](class-attributes.md)
