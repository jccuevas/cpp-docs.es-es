---
title: SafeGreaterThan | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeGreaterThan
dev_langs:
- C++
helpviewer_keywords:
- SafeGreaterThan function
ms.assetid: 32cecac9-ba88-43eb-a7a4-30e390456739
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8c67dbe68c26a306b59eaf20b741b6b061ac2192
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42596515"
---
# <a name="safegreaterthan"></a>SafeGreaterThan

Compara dos números.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename T, typename U>
inline bool SafeGreaterThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parámetros

[in] *t*  
El primer número que se compara. Esto debe ser de tipo `T`.

[in] *u*  
Segundo número que se va a comparar. Esto debe ser de tipo `U`.

## <a name="return-value"></a>Valor devuelto

**True** si *t* es mayor que *u*; de lo contrario **false**.

## <a name="remarks"></a>Comentarios

**SafeGreaterThan** amplía el operador de comparación normal por lo que le permite comparar dos tipos diferentes de números.

Este método forma parte de [Biblioteca SafeInt](../windows/safeint-library.md) y está diseñado para una operación de comparación único sin necesidad de crear una instancia de la [clase SafeInt](../windows/safeint-class.md).

> [!NOTE]
> Este método solo debe usarse cuando una operación matemática solo debe estar protegida. Si hay varias operaciones, se debe utilizar el `SafeInt` clase en lugar de llamar a las funciones individuales independientes.

Para obtener más información acerca de los tipos de plantilla `T` y `U`, consulte [SafeInt (funciones)](../windows/safeint-functions.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** safeint.h

**Namespace:** Microsoft::Utilities

## <a name="see-also"></a>Vea también

[SafeInt (funciones)](../windows/safeint-functions.md)  
[Biblioteca SafeInt](../windows/safeint-library.md)  
[SafeInt (clase)](../windows/safeint-class.md)  
[SafeLessThan](../windows/safelessthan.md)  
[SafeLessThanEquals](../windows/safelessthanequals.md)  
[SafeGreaterThanEquals](../windows/safegreaterthanequals.md)