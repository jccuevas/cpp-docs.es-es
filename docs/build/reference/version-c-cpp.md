---
title: VERSION (C/C++)
ms.date: 11/04/2016
f1_keywords:
- VERSION
helpviewer_keywords:
- VERSION .def file statement
ms.assetid: 3533b97c-5183-45f9-9ca8-4e63462b5d26
ms.openlocfilehash: abc0b751440d09dcaad7e449d7b151b479c51911
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815156"
---
# <a name="version-cc"></a>VERSION (C/C++)

Indica a LINK que ponga un número en el encabezado del archivo .exe o DLL.

```
VERSION major[.minor]
```

## <a name="remarks"></a>Comentarios

El *principales* y *menores* argumentos son números decimales comprendidos en el intervalo entre 0 y 65.535. El valor predeterminado es la versión 0.0.

Es una manera equivalente para especificar un número de versión con el [información de versión](version-version-information.md) (/ versión) opción.

## <a name="see-also"></a>Vea también

[Reglas para instrucciones de definición de módulos](rules-for-module-definition-statements.md)
