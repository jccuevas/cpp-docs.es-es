---
title: money_base (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- xlocmon/std::money_base
dev_langs:
- C++
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a33e60ff54c7ec03ef806f5104513c9838449190
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="moneybase-class"></a>money_base (Clase)

La clase describe una enumeración y una estructura común a todas las especializaciones de la clase de plantilla [moneypunct](../standard-library/moneypunct-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
struct pattern
{
   char field[_PATTERN_FIELD_SIZE];
};
```

## <a name="remarks"></a>Comentarios

La enumeración **part** describe los valores posibles de los elementos del campo de matriz en el patrón de estructura. Los valores de **part** son:

- **none** para buscar cero o más espacios o no generar nada.

- **sign** para buscar o generar un signo positivo o negativo.

- **space** para buscar cero o más espacios o generar un espacio.

- **symbol** para buscar o generar un símbolo de moneda.

- **value** para buscar o generar un valor monetario.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
