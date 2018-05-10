---
title: 'Implements:: fillarraywithiid (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::FillArrayWithIid
dev_langs:
- C++
helpviewer_keywords:
- FillArrayWithIid method
ms.assetid: b2e62e3f-0ab9-4c70-aad7-856268544f44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e020bd725d0c0f5c65ab1cfb38b45e2b8fbca62e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="implementsfillarraywithiid-method"></a>Implements::FillArrayWithIid (Método)
Inserta el identificador de interfaz especificado por el parámetro de plantilla actual de cero en el elemento de la matriz especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__forceinline static void FillArrayWithIid(  
   unsigned long &index,  
   _In_ IID* iids  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `index`  
 Índice de base cero que indica el elemento de matriz inicial para esta operación. Cuando se complete esta operación, `index` se incrementa en 1.  
  
 `iids`  
 Una matriz de tipo IID.  
  
## <a name="remarks"></a>Comentarios  
 Función auxiliar interno.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Implements (estructura)](../windows/implements-structure.md)