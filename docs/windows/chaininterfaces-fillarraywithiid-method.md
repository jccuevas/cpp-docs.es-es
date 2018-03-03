---
title: "Chaininterfaces:: Fillarraywithiid (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::FillArrayWithIid
dev_langs:
- C++
helpviewer_keywords:
- FillArrayWithIid method
ms.assetid: f1ce699c-dfb6-40a9-9ea0-e6703d3cf971
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 02e78ade52de45cfe06ba9d8cddfe0a2362d1bc9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="chaininterfacesfillarraywithiid-method"></a>ChainInterfaces::FillArrayWithIid (Método)
Almacena el identificador de interfaz definido por el `I0` parámetro de plantilla en una ubicación especificada de una matriz especificada de identificadores de interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__forceinline static void FillArrayWithIid(  
   _Inout_ unsigned long &index,  
   _In_ IID* iids  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `index`  
 Puntero a un valor de índice en el `iids` matriz.  
  
 `iids`  
 Una matriz de identificadores de interfaz.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ChainInterfaces (estructura)](../windows/chaininterfaces-structure.md)