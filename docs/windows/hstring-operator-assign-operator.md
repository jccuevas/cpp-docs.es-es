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
ms.openlocfilehash: 8e528bed14f3f6f3b35270975833bdd17fd777db
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422654"
---
# <a name="hstringoperator-operator"></a>HString::Operator= (Operador)

Mueve el valor de otro **HString** el objeto actual **HString** objeto.

## <a name="syntax"></a>Sintaxis

```cpp
HString& operator=(HString&& other) throw()  
```

### <a name="parameters"></a>Parámetros

*other*<br/>
Existente **HString** objeto.

## <a name="remarks"></a>Comentarios

El valor de la existente *otros* objeto se copia a la actual **HString** objeto y, a continuación, el *otros* se destruye el objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[HString (clase)](../windows/hstring-class.md)