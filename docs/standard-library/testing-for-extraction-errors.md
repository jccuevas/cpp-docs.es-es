---
title: Comprobar errores de extracción
ms.date: 11/04/2016
helpviewer_keywords:
- extraction errors
ms.assetid: 6a681028-adba-4557-8f7b-f137932905f8
ms.openlocfilehash: db551a21fd33665d83b11373f040be158406d492
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453663"
---
# <a name="testing-for-extraction-errors"></a>Comprobar errores de extracción

Las funciones de procesamiento de errores de salida, que se describen en [Funciones de procesamiento de errores](../standard-library/output-file-stream-member-functions.md), se aplican a los flujos de entrada. Es importante probar si hay errores durante la extracción. Considere esta instrucción:

```cpp
cin>> n;
```

Si `n` es un entero con signo, un valor mayor que 32.767 (el valor máximo permitido o MAX_INT) establece el bit `fail` de la secuencia y el objeto `cin` se vuelve inutilizable. Todas las extracciones posteriores generan una devolución inmediata sin ningún valor almacenado.

## <a name="see-also"></a>Vea también

[Flujos de entrada](../standard-library/input-streams.md)
