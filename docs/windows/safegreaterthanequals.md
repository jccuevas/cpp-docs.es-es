---
title: SafeGreaterThanEquals | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeGreaterThanEquals
dev_langs:
- C++
helpviewer_keywords:
- SafeGreaterThanEquals function
ms.assetid: 43312fa9-d925-4f9f-a352-a190c02b3005
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4bafae070d3ff9fe80070e3598cd36867abcf830
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707205"
---
# <a name="safegreaterthanequals"></a>SafeGreaterThanEquals

Compara dos números.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename T, typename U>
inline bool SafeGreaterThanEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parámetros

*t*<br/>
[in] El primer número que se compara. Esto debe ser de tipo `T`.

*u*<br/>
[in] Segundo número que se va a comparar. Esto debe ser de tipo `U`.

## <a name="return-value"></a>Valor devuelto

**True** si *t* es mayor o igual a *u*; de lo contrario **false**.

## <a name="remarks"></a>Comentarios

**SafeGreaterThanEquals** mejora el operador de comparación estándar porque permite comparar dos tipos diferentes de números.

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
[SafeGreaterThan](../windows/safegreaterthan.md)  
[SafeLessThanEquals](../windows/safelessthanequals.md)  
[SafeLessThan](../windows/safelessthan.md)