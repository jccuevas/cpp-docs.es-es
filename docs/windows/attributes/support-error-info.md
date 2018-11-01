---
title: support_error_info (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.support_error_info
helpviewer_keywords:
- support_error_info attribute
ms.assetid: 20a2b55c-4738-4b35-a71d-e5e9c3a7e3bc
ms.openlocfilehash: 8aed647677b8c8d26fdca522c10ec9ecee9f87c9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626015"
---
# <a name="supporterrorinfo"></a>support_error_info

Implementa compatibilidad para devolver errores detallados.

## <a name="syntax"></a>Sintaxis

```cpp
[ support_error_info(error_interface=uuid) ]
```

### <a name="parameters"></a>Parámetros

*error_interface*<br/>
El identificador de la interfaz que implementa `IErrorInfo`.

## <a name="remarks"></a>Comentarios

El atributo de C++ **support_error_info** implementa compatibilidad para devolver al cliente errores detallados y contextuales detectados por el objeto de destino. Para el objeto compatible con errores, los métodos de la `IErrorInfo` interfaz debe implementarse mediante el objeto. Para obtener más información, consulte [Compatibilidad con IDispatch e IErrorInfo](../../atl/supporting-idispatch-and-ierrorinfo.md).

Este atributo agrega la clase [ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md) como una clase base al objeto de destino. Esto da como resultado una implementación predeterminada de `ISupportErrorInfo` y puede usarse cuando una sola interfaz genera errores en un objeto.

## <a name="example"></a>Ejemplo

El código siguiente agrega compatibilidad predeterminada con la `ISupportErrorInfo` interfaz a la `CMyClass` objeto.

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
|**Se aplica a**|**clase**|
|**Reiterativo**|Sí|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos COM](com-attributes.md)<br/>
[Atributos de clase](class-attributes.md)