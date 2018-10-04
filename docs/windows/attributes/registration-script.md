---
title: registration_script (atributo de COM de C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.registration_script
dev_langs:
- C++
helpviewer_keywords:
- registration_script attribute
ms.assetid: 786f8072-9187-4163-a979-7a604dd4c888
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: edc9d5aa1d7c49de34ee3dbb02d2a55542962a50
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48792414"
---
# <a name="registrationscript"></a>registration_script

Ejecuta el script de registro personalizado especificado.

## <a name="syntax"></a>Sintaxis

```cpp
[ registration_script(script) ]
```

### <a name="parameters"></a>Parámetros

*secuencia de comandos*<br/>
La ruta de acceso completa a un archivo de script (.rgs) de registro personalizado. Un valor de **ninguno**, tales como `script = "none"`, indica que la coclase no tiene ningún requisito de registro.

## <a name="remarks"></a>Comentarios

El **registration_script** atributo de C++ ejecuta el script de registro personalizado especificado por *script*. Si no se especifica este atributo, se usa un archivo .rgs estándar (que contiene información para registrar el componente). Para obtener más información sobre los archivos .rgs, consulte [el componente de registro de ATL (registrador)](../../atl/atl-registry-component-registrar.md).

Este atributo requiere que el [coclase](coclass.md), [progid](progid.md), o [vi_progid](vi-progid.md) atributo (u otro atributo que implique uno de estos) se aplica también al mismo elemento.

## <a name="example"></a>Ejemplo

El código siguiente especifica que el componente tiene un script de registro denominado cpp_attr_ref_registration_script.rgs.

```cpp
// cpp_attr_ref_registration_script.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="REG")];

[object, uuid("d9cd196b-6836-470b-9b9b-5b04b828e5b0")]
__interface IFace {};

// requires "cpp_attr_ref_registration_script.rgs"
// create sample .RGS file "cpp_attr_ref_registration_script.rgs" if it does not exist
[ coclass, registration_script(script="cpp_attr_ref_registration_script.rgs"),
  uuid("50d3ad42-3601-4f26-8cfe-0f1f26f98f67")]
class CMyClass:public IFace {};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|No|
|**Atributos requeridos**|Una o varias de las siguientes acciones: `coclass`, `progid`, o `vi_progid`.|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, vea [contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos COM](com-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[rdx](rdx.md)  