---
title: Método Hstringreference | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 179d9b14-1ced-4b16-b297-19ca1e92a462
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 22886621760ed53649d26180877b1463ec2d3f2d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592169"
---
# <a name="hstringreferencecopyto-method"></a>HStringReference::CopyTo (Método)

Copia actual **HStringReference** objeto a un objeto HSTRING.

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

[HStringReference (clase)](../windows/hstringreference-class.md)