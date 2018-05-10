---
title: Estructura identity | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- utility/std::identity
dev_langs:
- C++
helpviewer_keywords:
- identity class
- identity structure
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83180020c20f78c16af0b1b33bada91936b6af9b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="identity-structure"></a>identity (Estructura)

Estructura que proporciona una definición de tipo como parámetro de plantilla.

## <a name="syntax"></a>Sintaxis

```cpp
struct identity {
   typedef Type type;
   Type operator()(const Type& left) const;
   };
```
### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|`left`|Valor que se va a identificar.|

## <a name="remarks"></a>Comentarios

La clase contiene la definición de tipo público `type`, que es igual que el tipo de parámetro de plantilla. Se usa junto con la función de plantilla [forward](../standard-library/utility-functions.md#forward) para asegurarse de que un parámetro de función tiene el tipo deseado.

Para garantizar la compatibilidad con código antiguo, la clase también define la función identity `operator()` que devuelve su argumento `left`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<utility>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[\<utility>](../standard-library/utility.md)<br/>
