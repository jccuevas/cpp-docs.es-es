---
title: "Chaininterfaces:: Cancastto (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::ChainInterfaces::CanCastTo
dev_langs: C++
helpviewer_keywords: CanCastTo method
ms.assetid: 8be44875-53ed-494b-91a0-0f8e399685bb
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f614ec0eff2b448c8f20c88557f6228f85a770bd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
 `true`Si todas las operaciones de conversión se realizó correctamente; en caso contrario, `false`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ChainInterfaces (estructura)](../windows/chaininterfaces-structure.md)