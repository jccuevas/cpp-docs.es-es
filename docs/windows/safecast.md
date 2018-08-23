---
title: SafeCast | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeCast
dev_langs:
- C++
helpviewer_keywords:
- SafeCast function
ms.assetid: 55316729-8456-403a-9f96-59d4038f67af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 27c049b57d51f173e2a388e48f24d9b9674ae46b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606102"
---
# <a name="safecast"></a>SafeCast

Convierte un tipo de número a otro tipo.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename T, typename U>
inline bool SafeCast (
   const T From,
   U& To
);
```

### <a name="parameters"></a>Parámetros

[in] *Desde*  
Para convertir el número de origen. Esto debe ser de tipo `T`.

[out] *a*  
Una referencia al nuevo tipo de número. Esto debe ser de tipo `U`.

## <a name="return-value"></a>Valor devuelto

**True** si se produce ningún error; **false** si se produce un error.

## <a name="remarks"></a>Comentarios

Este método forma parte de [Biblioteca SafeInt](../windows/safeint-library.md) y está diseñado para una operación de conversión única sin crear una instancia de la [clase SafeInt](../windows/safeint-class.md).

> [!NOTE]
> Este método solo debe usarse cuando se debe proteger una sola operación. Si hay varias operaciones, se debe utilizar el `SafeInt` clase en lugar de llamar a las funciones individuales independientes.

Para obtener más información acerca de los tipos de plantilla T y U, consulte [SafeInt (funciones)](../windows/safeint-functions.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** safeint.h

**Namespace:** Microsoft::Utilities

## <a name="see-also"></a>Vea también

[SafeInt (funciones)](../windows/safeint-functions.md)  
[Biblioteca SafeInt](../windows/safeint-library.md)  
[SafeInt (clase)](../windows/safeint-class.md)