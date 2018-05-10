---
title: 'Comptr:: Releaseandgetaddressof (método) | Documentos de Microsoft'
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
ms.openlocfilehash: 32d846a1fc41596812ca6e8578f25f9ae8115182
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="comptrreleaseandgetaddressof-method"></a>ComPtr::ReleaseAndGetAddressOf (Método)
Libera la interfaz asociada a esta ComPtr y después recupera la dirección del miembro de datos [ptr_](../windows/comptr-ptr-data-member.md) , que contiene un puntero a la interfaz que se liberó.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
T** ReleaseAndGetAddressOf();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 La dirección de la [ptr_](../windows/comptr-ptr-data-member.md) miembro de datos de esta ComPtr.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ComPtr (clase)](../windows/comptr-class.md)   
 [ComPtr::ptr_ (miembro de datos)](../windows/comptr-ptr-data-member.md)