---
title: Comprobar errores de extracción | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- extraction errors
ms.assetid: 6a681028-adba-4557-8f7b-f137932905f8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc84277b654a79eebd38461c3ee83aefd533e4a8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33853903"
---
# <a name="testing-for-extraction-errors"></a>Comprobar errores de extracción

Las funciones de procesamiento de errores de salida, que se describen en [Funciones de procesamiento de errores](../standard-library/output-file-stream-member-functions.md), se aplican a los flujos de entrada. Es importante probar si hay errores durante la extracción. Considere esta instrucción:

```cpp
cin>> n;
```

Si `n` es un entero con signo, un valor mayor que 32.767 (el valor máximo permitido o MAX_INT) establece el bit `fail` de la secuencia y el objeto `cin` se vuelve inutilizable. Todas las extracciones posteriores generan una devolución inmediata sin ningún valor almacenado.

## <a name="see-also"></a>Vea también

[Flujos de entrada](../standard-library/input-streams.md)<br/>
