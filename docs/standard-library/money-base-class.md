---
title: money_base (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocmon/std::money_base
dev_langs:
- C++
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 805045e4ea63f153e9a35b0d4b068bd69874b93f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33864091"
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
