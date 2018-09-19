---
title: 'Hstringreference:: operator = (operador) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=
dev_langs:
- C++
ms.assetid: ea100ed3-e566-4c9e-b6a8-f296088dea9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7045229cc15304a88253f97e1ad3c9f171f139a0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597133"
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator= (Operador)

Mueve el valor de otro **HStringReference** el objeto actual **HStringReference** objeto.

## <a name="syntax"></a>Sintaxis

```cpp
HStringReference& operator=(HStringReference&& other) throw()  
```

### <a name="parameters"></a>Parámetros

*other*  
Existente **HStringReference** objeto.

## <a name="remarks"></a>Comentarios

El valor de la existente *otros* objeto se copia a la actual **HStringReference** objeto y, a continuación, el *otros* se destruye el objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[HStringReference (clase)](../windows/hstringreference-class.md)