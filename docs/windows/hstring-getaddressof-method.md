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
ms.openlocfilehash: 4ea49833107bf58443bf4a8238229d1d63a86742
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010352"
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