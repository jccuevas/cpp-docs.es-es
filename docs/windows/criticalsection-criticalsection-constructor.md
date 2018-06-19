---
title: Constructor CriticalSection | Documentos de Microsoft
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
ms.openlocfilehash: d86c80d169cb6d9794f163290c30bf1b2563588b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33870902"
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
