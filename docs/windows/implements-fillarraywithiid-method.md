---
title: Fillarraywithiid (método) | Microsoft Docs
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
ms.openlocfilehash: f374c945312e41fd54b525dc0cb7cd84ce84985d
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018899"
---
# <a name="implementsfillarraywithiid-method"></a>Implements::FillArrayWithIid (Método)
Inserta el Id. de interfaz especificado por el parámetro de plantilla actual de cero en el elemento de matriz especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
__forceinline static void FillArrayWithIid(  
   unsigned long &index,  
   _In_ IID* iids  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *index*  
 Índice de base cero que indica el elemento de matriz inicial para esta operación. Cuando se complete esta operación, *índice* se incrementa en 1.  
  
 *IID*  
 Una matriz de tipo IID.  
  
## <a name="remarks"></a>Comentarios  
 Función auxiliar interno.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Implements (estructura)](../windows/implements-structure.md)