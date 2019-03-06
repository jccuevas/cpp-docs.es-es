---
title: VERSION (C/C++)
ms.date: 11/04/2016
f1_keywords:
- VERSION
helpviewer_keywords:
- VERSION .def file statement
ms.assetid: 3533b97c-5183-45f9-9ca8-4e63462b5d26
ms.openlocfilehash: 6d275e1e191e0550143dd5e7a828b734bba0fc96
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414062"
---
# <a name="version-cc"></a>VERSION (C/C++)

Indica a LINK que ponga un número en el encabezado del archivo .exe o DLL.

```
VERSION major[.minor]
```

## <a name="remarks"></a>Comentarios

El *principales* y *menores* argumentos son números decimales comprendidos en el intervalo entre 0 y 65.535. El valor predeterminado es la versión 0.0.

Es una manera equivalente para especificar un número de versión con el [información de versión](../../build/reference/version-version-information.md) (/ versión) opción.

## <a name="see-also"></a>Vea también

[Reglas para instrucciones de definición de módulos](../../build/reference/rules-for-module-definition-statements.md)
