---
title: subprocesamiento (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.threading
helpviewer_keywords:
- threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
ms.openlocfilehash: b249eaf61266ed9964e44f6f0ad1c2f12a1b1067
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214505"
---
# <a name="threading-c"></a>threading (C++)

Especifica el modelo de subprocesos para un objeto COM.

## <a name="syntax"></a>Sintaxis

```cpp
[ threading(model=enumeration) ]
```

### <a name="parameters"></a>Parámetros

*model*<br/>
Opta Uno de los siguientes modelos de subprocesos:

- `apartment` (subprocesamiento controlado)

- `neutral` (componentes de .NET Framework sin interfaz de usuario)

- `single` (subprocesamiento simple)

- `free` (subprocesamiento libre)

- `both` (subprocesamiento controlado y libre)

El valor predeterminado es `apartment`.

## <a name="remarks"></a>Observaciones

El **threading** C++ atributo Threading no aparece en el archivo. idl generado, pero se utilizará en la implementación del objeto com.

En los proyectos ATL, si el atributo [CoClass](coclass.md) también está presente, el modelo de subprocesos especificado por *Model* se pasa como parámetro de plantilla a la clase [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) , insertado por el atributo `coclass`.

El atributo **Threading** también protege el acceso a un [event_source](event-source.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo con [licencia](licensed.md) para obtener un ejemplo de uso de **subprocesos**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|No|
|**Atributos requeridos**|**coclass**|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos COM](com-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Compatibilidad del código antiguo con multithreading (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)<br/>
[Apartamentos neutros](/windows/win32/cossdk/neutral-apartments)
