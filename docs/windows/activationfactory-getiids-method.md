---
title: Método Activationfactory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory::GetIids
dev_langs:
- C++
helpviewer_keywords:
- GetIids method
ms.assetid: 0983d709-d155-4d65-aae4-5b2c8bb0fede
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aaaa8d5bb0a88b9078c60fa61608e52fafd5baac
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643516"
---
# <a name="activationfactorygetiids-method"></a>ActivationFactory::GetIids (Método)
Recupera una matriz de identificadores de interfaz implementada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
STDMETHOD(  
   GetIids  
)(_Out_ ULONG *iidCount, _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);  
```  
  
### <a name="parameters"></a>Parámetros  
 *iidCount*  
 Cuando finalice esta operación, el número de identificadores de interfaz en el *IID* matriz.  
  
 *IID*  
 Cuando se complete esta operación, una matriz de implementa los identificadores de interfaz.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error. E_OUTOFMEMORY es un valor HRESULT de error posibles.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ActivationFactory (clase)](../windows/activationfactory-class.md)