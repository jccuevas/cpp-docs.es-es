---
title: Estructura hash (biblioteca estándar de C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- thread/std::hash
dev_langs:
- C++
ms.assetid: 4a8bf5bc-4334-4070-936b-98585f8a073b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f2e9fdbef911a0160ff42925a9c7984f0211069
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="hash-structure-c-standard-library"></a>Estructura hash (biblioteca estándar de C++)

Define una función miembro que devuelve un valor que se determina de forma exclusiva mediante `Val`. La función miembro define una función [hash](../standard-library/hash-class.md) adecuada para asignar valores de tipo `thread::id` a una distribución de valores de índice.

## <a name="syntax"></a>Sintaxis

```cpp
template <>
struct hash<thread::id> :
    public unary_function<thread::id, size_t>
{
    size_t operator()(thread::id Val) const;


};
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<subproceso >

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<thread>](../standard-library/thread.md)<br/>
[unary_function (Struct)](../standard-library/unary-function-struct.md)<br/>
