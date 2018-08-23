---
title: SafeEquals | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeEquals
dev_langs:
- C++
helpviewer_keywords:
- SafeEquals function
ms.assetid: 6019627d-f170-413b-9abd-2b5b34396a72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2b0c2bb91f21b48554ca523a3523e82eee09d2fe
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600588"
---
# <a name="safeequals"></a>SafeEquals

Compara dos números para determinar si son iguales.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename T, typename U>
inline bool SafeEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parámetros

[in] *t*  
El primer número que se compara. Debe ser de tipo T.

[in] *u*  
Segundo número que se va a comparar. Debe ser de tipo U.

## <a name="return-value"></a>Valor devuelto

**True** si *t* y *u* son iguales; en caso contrario **false**.

## <a name="remarks"></a>Comentarios

El método mejora `==` porque **SafeEquals** permite comparar dos tipos diferentes de números.

Este método forma parte de [Biblioteca SafeInt](../windows/safeint-library.md) y está diseñado para una operación de comparación único sin necesidad de crear una instancia de la [clase SafeInt](../windows/safeint-class.md).

> [!NOTE]
> Este método solo debe usarse cuando una operación matemática solo debe estar protegida. Si hay varias operaciones, se debe utilizar el `SafeInt` clase en lugar de llamar a las funciones individuales independientes.

Para obtener más información acerca de los tipos de plantilla T y U, consulte [SafeInt (funciones)](../windows/safeint-functions.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** safeint.h

**Namespace:** Microsoft::Utilities

## <a name="see-also"></a>Vea también

[SafeInt (funciones)](../windows/safeint-functions.md)  
[Biblioteca SafeInt](../windows/safeint-library.md)  
[SafeInt (clase)](../windows/safeint-class.md)  
[SafeNotEquals](../windows/safenotequals.md)