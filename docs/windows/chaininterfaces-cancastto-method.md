---
title: 'Chaininterfaces:: Cancastto (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: 8be44875-53ed-494b-91a0-0f8e399685bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c2286c347fbd68f34fac807e80facca0a0286aa6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="chaininterfacescancastto-method"></a>ChainInterfaces::CanCastTo (Método)
Indica si el identificador de interfaz especificado se puede convertir a cada una de las especializaciones definidas por los parámetros de plantilla no es el predeterminado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__forceinline bool CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `riid`  
 Id. de interfaz.  
  
 `ppv`  
 Un puntero al último identificador de interfaz que se convirtió correctamente.  
  
## <a name="return-value"></a>Valor devuelto  
 `true` Si todas las operaciones de conversión se realizó correctamente; en caso contrario, `false`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ChainInterfaces (estructura)](../windows/chaininterfaces-structure.md)