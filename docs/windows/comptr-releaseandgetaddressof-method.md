---
title: Releaseandgetaddressof (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf
dev_langs:
- C++
helpviewer_keywords:
- ReleaseAndGetAddressOf method
ms.assetid: 3751dcb4-d50e-432c-89e4-e736be34d434
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3bded6992abc5b22e2c02a3364431a3f68b76ad6
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649853"
---
# <a name="comptrreleaseandgetaddressof-method"></a>ComPtr::ReleaseAndGetAddressOf (Método)
Libera la interfaz asociada a este **ComPtr** y, a continuación, recupera la dirección de la [ptr_](../windows/comptr-ptr-data-member.md) miembro de datos que contiene un puntero a la interfaz que se publicó.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
T** ReleaseAndGetAddressOf();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 La dirección de la [ptr_](../windows/comptr-ptr-data-member.md) miembro de datos de este **ComPtr**.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ComPtr (clase)](../windows/comptr-class.md)   
 [ComPtr::ptr_ (miembro de datos)](../windows/comptr-ptr-data-member.md)