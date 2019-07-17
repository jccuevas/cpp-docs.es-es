---
title: identity (Estructura)
ms.date: 11/04/2016
f1_keywords:
- utility/std::identity
helpviewer_keywords:
- identity class
- identity structure
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
ms.openlocfilehash: 49b2c1eb3ca03f9bf9199bdbca49348866ff0a7e
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246162"
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

*Izquierda*\
Valor que se va a identificar.

## <a name="remarks"></a>Comentarios

La clase contiene la definición de tipo público `type`, que es igual que el tipo de parámetro de plantilla. Se usa junto con la función de plantilla [forward](../standard-library/utility-functions.md#forward) para asegurarse de que un parámetro de función tiene el tipo deseado.

Para la compatibilidad con el código anterior, la clase también define la función identity `operator()` que devuelve su argumento *izquierdo*.
