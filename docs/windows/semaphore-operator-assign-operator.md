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
ms.openlocfilehash: fbce88be7f7b83c22964438bc4ea7a783754fb63
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609013"
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

*h*  
Referencia de valor r a un **semáforo** objeto.

## <a name="return-value"></a>Valor devuelto

Una referencia a la actual **semáforo** objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también
[Semaphore (clase)](../windows/semaphore-class.md)