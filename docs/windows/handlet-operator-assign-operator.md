---
title: 'Handlet:: operator = (operador) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: 9e42dcca-30fa-4e8b-8954-802fd64a5595
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4c6aeca188f51f35c739c32f5290aac011781b41
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396901"
---
# <a name="handletoperator-operator"></a>HandleT::operator= (Operador)

Mueve el valor del elemento especificado **HandleT** el objeto actual **HandleT** objeto.

## <a name="syntax"></a>Sintaxis

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>Parámetros

*h*<br/>
Una referencia rvalue a un identificador.

## <a name="return-value"></a>Valor devuelto

Una referencia a la actual **HandleT** objeto.

## <a name="remarks"></a>Comentarios

Esta operación invalida la **HandleT** objeto especificado por el parámetro *h*.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[HandleT (clase)](../windows/handlet-class.md)