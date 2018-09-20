---
title: SafeAdd | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeAdd
dev_langs:
- C++
helpviewer_keywords:
- SafeAdd function
ms.assetid: 3f82b91d-59fe-4ee1-873b-d056182fa8be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2ddf4f69c3c897c8f462554ce6a9db6b2a03408f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400593"
---
# <a name="safeadd"></a>SafeAdd

Suma dos números de forma que protege contra el desbordamiento.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename T, typename U>
inline bool SafeAdd (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parámetros

*t*<br/>
[in] Primer número que se va a agregar. Debe ser de tipo T.

*u*<br/>
[in] Segundo número que se va a agregar. Debe ser de tipo U.

*Resultado*<br/>
[out] El parámetro donde **SafeAdd** almacena el resultado.

## <a name="return-value"></a>Valor devuelto

**True** si se produce ningún error; **false** si se produce un error.

## <a name="remarks"></a>Comentarios

Este método forma parte de [Biblioteca SafeInt](../windows/safeint-library.md) y está diseñado para una operación de suma única sin crear una instancia de la [clase SafeInt](../windows/safeint-class.md).

> [!NOTE]
> Este método solo debe usarse cuando una operación matemática solo debe estar protegida. Si hay varias operaciones, se debe utilizar el `SafeInt` clase en lugar de llamar a las funciones individuales independientes.

Para obtener más información acerca de los tipos de plantilla T y U, consulte [SafeInt (funciones)](../windows/safeint-functions.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** safeint.h

**Namespace:** Microsoft::Utilities

## <a name="see-also"></a>Vea también

[SafeInt (funciones)](../windows/safeint-functions.md)<br/>
[Biblioteca SafeInt](../windows/safeint-library.md)<br/>
[SafeInt (clase)](../windows/safeint-class.md)<br/>
[SafeSubtract](../windows/safesubtract.md)