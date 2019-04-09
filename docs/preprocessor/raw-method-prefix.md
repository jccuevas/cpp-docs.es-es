---
title: raw_method_prefix
ms.date: 03/27/2019
f1_keywords:
- raw_method_prefix
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
ms.openlocfilehash: 963e04752dcb797343550d9b89f778bfe0e8a593
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59021416"
---
# <a name="rawmethodprefix"></a>raw_method_prefix

**Específicos de C++**

Especifica otro prefijo para evitar conflictos de nombres.

## <a name="syntax"></a>Sintaxis

```
raw_method_prefix("Prefix")
```

### <a name="parameters"></a>Parámetros

*Prefijo*<br/>
El prefijo que se va a usar.

## <a name="remarks"></a>Comentarios

Métodos y propiedades de bajo nivel son expuestos por funciones miembro denominadas con el prefijo predeterminado **raw_** para evitar conflictos con las funciones de miembro alto nivel de control de errores.

> [!NOTE]
> Los efectos de la **raw_method_prefix** atributo no se cambiará por la presencia de la [raw_interfaces_only](raw-interfaces-only.md) atributo. El **raw_method_prefix** siempre tiene prioridad sobre `raw_interfaces_only` especifica un prefijo. Si ambos atributos se usan en la misma `#import` instrucción y, a continuación, el prefijo especificado por el **raw_method_prefix** se usa el atributo.

**Específicos de C++: END**

## <a name="see-also"></a>Vea también

[Atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)