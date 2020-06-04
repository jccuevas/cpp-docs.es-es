---
title: immediatebind (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.immediatebind
helpviewer_keywords:
- immediatebind attribute
ms.assetid: 186d40e6-9166-4d0c-9853-4e7e4d25226f
ms.openlocfilehash: d0fb85a3f5642bc5fffcad29892ca15bb13a1ce0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166919"
---
# <a name="immediatebind"></a>immediatebind

Indica que se notificará inmediatamente a la base de datos todos los cambios efectuados en una propiedad de un objeto enlazado a datos.

## <a name="syntax"></a>Sintaxis

```cpp
[immediatebind]
```

## <a name="remarks"></a>Observaciones

El atributo **immediatebind** C++ tiene la misma funcionalidad que el atributo MIDL [immediatebind](/windows/win32/Midl/immediatebind) .

## <a name="example"></a>Ejemplo

Vea [enlazable](bindable.md) para obtener un ejemplo de cómo usar **immediatebind**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[defaultbind](defaultbind.md)<br/>
[displaybind](displaybind.md)<br/>
[requestedit](requestedit.md)
