---
title: 'Hstringreference:: operator&lt; operador | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator<
dev_langs:
- C++
ms.assetid: 55aa48e8-7c96-4123-9ebe-42b4cd8b9377
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ee7edbee285df6da752e875ac4d86a74e8f7893d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594146"
---
# <a name="hstringreferenceoperatorlt-operator"></a>Hstringreference:: operator&lt; operador

Indica si el primer parámetro es menor que el segundo parámetro.

## <a name="syntax"></a>Sintaxis

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()  
```

### <a name="parameters"></a>Parámetros

*LHS*  
El primer parámetro para comparar. *LHS* puede ser una referencia a un **HStringReference**.

*RHS*  
El segundo parámetro para comparar.  *RHS* puede ser una referencia a un **HStringReference**.

## <a name="return-value"></a>Valor devuelto

**True** si el *lhs* parámetro es menor que el *rhs* parámetro; en caso contrario, **false**.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[HStringReference (clase)](../windows/hstringreference-class.md)