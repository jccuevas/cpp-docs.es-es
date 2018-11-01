---
title: raw_method_prefix
ms.date: 10/18/2018
f1_keywords:
- raw_method_prefix
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
ms.openlocfilehash: 4169b4e23049bf1cf2c61eaefba619169e0ce377
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467777"
---
# <a name="rawmethodprefix"></a>raw_method_prefix

**Específicos de C++**

Especifica otro prefijo para evitar conflictos de nombres.

## <a name="syntax"></a>Sintaxis

```
raw_method_prefix("Prefix")
```

### <a name="parameters"></a>Parámetros

*Prefix*<br/>
El prefijo que se va a usar.

## <a name="remarks"></a>Comentarios

Métodos y propiedades de bajo nivel son expuestos por funciones miembro denominadas con el prefijo predeterminado **raw_** para evitar conflictos con las funciones de miembro alto nivel de control de errores.

> [!NOTE]
> Los efectos de la **raw_method_prefix** atributo no se cambiará por la presencia de la [raw_interfaces_only](#_predir_raw_interfaces_only) atributo. El **raw_method_prefix** siempre tiene prioridad sobre `raw_interfaces_only` especifica un prefijo. Si ambos atributos se usan en la misma `#import` instrucción y, a continuación, el prefijo especificado por el **raw_method_prefix** se usa el atributo.

**FIN de específicos de C++**

## <a name="see-also"></a>Vea también

[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)