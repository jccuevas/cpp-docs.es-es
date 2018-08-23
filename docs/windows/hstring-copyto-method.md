---
title: Método hstring | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: a1fd2ef0-e175-4c18-927b-550e02a89e43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4e2a4ce5a2952a990ee3a2d934d6207656a57376
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592139"
---
# <a name="hstringcopyto-method"></a>HString::CopyTo (Método)

Copia actual **HString** objeto a un objeto HSTRING.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>Parámetros

*str*  
La HSTRING que recibe la copia.

## <a name="remarks"></a>Comentarios

Este método llama a la [WindowsDuplicateString](http://msdn.microsoft.com/library/br224634.aspx) función.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[HString (clase)](../windows/hstring-class.md)