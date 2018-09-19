---
title: Getaddressof (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::GetAddressOf
dev_langs:
- C++
ms.assetid: 6050decf-5f99-49f0-9497-1c8192c485ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e327e2818903396c154be7406ec325695b6b6982
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613370"
---
# <a name="hstringgetaddressof-method"></a>HString::GetAddressOf (Método)

Recupera un puntero al identificador HSTRING subyacente.

## <a name="syntax"></a>Sintaxis

```cpp
HSTRING* GetAddressOf() throw()  
```

## <a name="return-value"></a>Valor devuelto

Puntero al identificador HSTRING subyacente.

## <a name="remarks"></a>Comentarios

Después de realizar esta operación, se destruye el valor de cadena del identificador HSTRING subyacente.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[HString (clase)](../windows/hstring-class.md)