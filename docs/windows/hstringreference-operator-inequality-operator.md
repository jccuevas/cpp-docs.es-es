---
title: 'Hstringreference:: operator! = (operador) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator!=
dev_langs:
- C++
ms.assetid: 01ab6691-1fc7-4feb-85f0-fe795593a160
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 996ead81a72fb3cc58544576059a8347972e2a6b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429076"
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator!= (Operador)

Indica si los dos parámetros no son iguales.

## <a name="syntax"></a>Sintaxis

```cpp
inline bool operator==(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()

inline bool operator!=(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()  
```

### <a name="parameters"></a>Parámetros

*LHS*<br/>
El primer parámetro para comparar. *LHS* puede ser un **HStringReference** objeto o un identificador HSTRING.

*RHS*<br/>
El segundo parámetro para comparar.  *RHS* puede ser un **HStringReference** objeto o un identificador HSTRING.

## <a name="return-value"></a>Valor devuelto

**True** si el *lhs* y *rhs* parámetros no son iguales; en caso contrario, **false**.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[HStringReference (clase)](../windows/hstringreference-class.md)