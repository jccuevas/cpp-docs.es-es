---
title: 'Semaphore:: operator = (operador) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: ea19839f-91f0-4b00-a35b-5728fcba4981
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1b35268cd883245b125aa7c87919124b29451ff1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420327"
---
# <a name="semaphoreoperator-operator"></a>Semaphore::operator= (Operador)

Mueve el identificador especificado de un **semáforo** el objeto actual **semáforo** objeto.

## <a name="syntax"></a>Sintaxis

```cpp
Semaphore& operator=(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>Parámetros

*h*<br/>
Referencia de valor r a un **semáforo** objeto.

## <a name="return-value"></a>Valor devuelto

Una referencia a la actual **semáforo** objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[Semaphore (clase)](../windows/semaphore-class.md)