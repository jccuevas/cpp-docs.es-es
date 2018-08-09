---
title: Constructor CriticalSection | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CriticalSection, constructor
ms.assetid: 930b89be-4d74-46bd-8879-5dd4d15bcbd0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f87f95a0683f6b4440d2be8b770902a7e4ecde59
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644299"
---
# <a name="criticalsectioncriticalsection-constructor"></a>CriticalSection::CriticalSection (Constructor)
Inicializa un objeto de sincronización que es similar a un objeto de exclusión mutua, pero se puede usar solo los subprocesos de un único proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
explicit CriticalSection(  
   ULONG spincount = 0  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *SpinCount*  
 El recuento circular para el objeto de sección crítica. El valor predeterminado es 0.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de las secciones críticas y spincounts, consulte el `InitializeCriticalSectionAndSpinCount` funcionando en el **sincronización** sección de la documentación de API de Windows.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [CriticalSection (clase)](../windows/criticalsection-class.md)