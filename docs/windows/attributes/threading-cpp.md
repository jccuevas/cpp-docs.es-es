---
title: Threading (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.threading
helpviewer_keywords:
- threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
ms.openlocfilehash: cdebf06a62ebbd1d8648b9777fe200bc7a373261
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407242"
---
# <a name="threading-c"></a>threading (C++)

Especifica el modelo de subprocesos para un objeto COM.

## <a name="syntax"></a>Sintaxis

```cpp
[ threading(model=enumeration) ]
```

### <a name="parameters"></a>Parámetros

*model*<br/>
(Opcional) Uno de los modelos de subprocesamiento siguientes:

- `apartment` (apartamento de subproceso)

- `neutral` (Componentes de .NET framework sin interfaz de usuario)

- `single` (ejecución de subprocesos simple)

- `free` (subprocesamiento libre)

- `both` (apartamento y subprocesamiento libre)

El valor predeterminado es `apartment`.

## <a name="remarks"></a>Comentarios

El **threading** atributo de C++ no aparece en el archivo .idl generado, pero se utilizará en la implementación de su objeto COM.

En los proyectos ATL, si la [coclase](coclass.md) también está presente, el atributo especificado por el modelo de subprocesos *modelo* se pasa como parámetro de plantilla para el [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) clase , inserta el `coclass` atributo.

El **threading** atributo también protege el acceso a un [event_source](event-source.md).

## <a name="example"></a>Ejemplo

Consulte la [licencia](licensed.md) ejemplo para un ejemplo de uso de **threading**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|No|
|**Atributos requeridos**|**coclase**|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos COM](com-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Compatibilidad del código antiguo con multithreading (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)<br/>
[Apartamentos neutros](/windows/desktop/cossdk/neutral-apartments)