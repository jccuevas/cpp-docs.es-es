---
title: 'Hstring:: operator = (operador) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator=
dev_langs:
- C++
ms.assetid: 8e68c1ff-bc57-4526-810e-af3c284b4e30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9294650db7a1b18c2542603988952a80b3f1905d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598550"
---
# <a name="hstringoperator-operator"></a>HString::Operator= (Operador)

Mueve el valor de otro **HString** el objeto actual **HString** objeto.

## <a name="syntax"></a>Sintaxis

```cpp
HString& operator=(HString&& other) throw()  
```

### <a name="parameters"></a>Parámetros

*other*  
Existente **HString** objeto.

## <a name="remarks"></a>Comentarios

El valor de la existente *otros* objeto se copia a la actual **HString** objeto y, a continuación, el *otros* se destruye el objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[HString (clase)](../windows/hstring-class.md)