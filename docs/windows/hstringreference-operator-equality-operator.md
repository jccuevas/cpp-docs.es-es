---
title: 'Hstringreference:: operator == (operador) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator==
dev_langs:
- C++
ms.assetid: cad3d52d-cd67-4194-a270-5239b1121a09
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b07df3dc50704a87883e1a387fe9c842c1732b54
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610538"
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator== (Operador)

Indica si los dos parámetros son iguales.

## <a name="syntax"></a>Sintaxis

```cpp
inline bool operator==(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()  
```

### <a name="parameters"></a>Parámetros

*LHS*  
El primer parámetro para comparar. *LHS* puede ser un **HStringReference** objeto o un identificador HSTRING.

*RHS*  
El segundo parámetro para comparar.  *RHS* puede ser un **HStringReference** objeto o un identificador HSTRING.

## <a name="return-value"></a>Valor devuelto

**True** si el *lhs* y *rhs* parámetros son iguales; en caso contrario, **false**.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[HStringReference (clase)](../windows/hstringreference-class.md)