---
title: Método Handletraits | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 3c631a7c-ccce-472a-b1da-aab8fa815c13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 561862427238a86dbb23ee05044c1d01558abab5
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647604"
---
# <a name="handletraitsclose-method"></a>HANDLETraits::Close (Método)
Cierra el identificador especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
inline static bool Close(  
   _In_ Type h  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *h*  
 Para cerrar el identificador.  
  
## <a name="return-value"></a>Valor devuelto  
 **True** si controlar *h* cerrado correctamente; en caso contrario, **false**.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** handletraits  
  
## <a name="see-also"></a>Vea también  
 [HANDLETraits (estructura)](../windows/handletraits-structure.md)