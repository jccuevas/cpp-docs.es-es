---
title: retval (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.retval
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
ms.openlocfilehash: 4ac6b72095620a3e857f2877d776e91b273e8f33
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566652"
---
# <a name="retval"></a>retval

Designa el parámetro que recibe el valor devuelto del miembro.

## <a name="syntax"></a>Sintaxis

```cpp
[retval]
```

## <a name="remarks"></a>Comentarios

El **retval** atributo de C++ tiene la misma funcionalidad que el [retval](/windows/desktop/Midl/retval) atributo MIDL.

**retval** debe aparecer en el último argumento en la declaración de una función.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [enlazable](bindable.md) para un ejemplo de uso de **retval**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Parámetro de interfaz, el método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|**out**|
|**Atributos no válidos**|**in**|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de parámetro](parameter-attributes.md)<br/>
[Atributos de método](method-attributes.md)