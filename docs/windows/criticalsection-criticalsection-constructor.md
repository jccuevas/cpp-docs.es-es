---
title: Constructor CriticalSection | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CriticalSection, constructor
ms.assetid: 930b89be-4d74-46bd-8879-5dd4d15bcbd0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 532a7b2e046bbdb64db118741a939dadb049f081
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="criticalsectioncriticalsection-constructor"></a>CriticalSection::CriticalSection (Constructor)
Inicializa un objeto de sincronización que es similar a un objeto de exclusión mutua, pero puede usar solo los subprocesos de un único proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
explicit CriticalSection(  
   ULONG spincount = 0  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `spincount`  
 El recuento de número para el objeto de sección crítica. El valor predeterminado es 0.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de las secciones críticas y spincounts, consulte el **InitializeCriticalSectionAndSpinCount** función en la sección de sincronización de la documentación de API de Windows.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [CriticalSection (clase)](../windows/criticalsection-class.md)
