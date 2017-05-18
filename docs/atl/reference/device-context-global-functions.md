---
title: Funciones globales del contexto de dispositivo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 8c71781519b965717acbcefab6fe6a183686caef
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="device-context-global-functions"></a>Funciones globales del contexto de dispositivo
Esta función crea un contexto de dispositivo para un dispositivo dado.  
  
|||  
|-|-|  
|[AtlCreateTargetDC](#atlcreatetargetdc)|Crea un contexto de dispositivo.|  
  
##  <a name="atlcreatetargetdc"></a>AtlCreateTargetDC  
 Crea un contexto de dispositivo para el dispositivo especificado en el [DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613) estructura.  
  
```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```  
  
### <a name="parameters"></a>Parámetros  
 *HDC*  
 [in] El identificador de un contexto de dispositivo existente o **NULL**.  
  
 `ptd`  
 [in] Un puntero a la **DVTARGETDEVICE** estructura que contiene información sobre el dispositivo de destino.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el identificador de contexto de dispositivo para el dispositivo especificado en el **DVTARGETDEVICE**. Si no se especifica ningún dispositivo, devuelve el identificador para el dispositivo de pantalla de forma predeterminada.  
  
### <a name="remarks"></a>Comentarios  
 Si la estructura es **NULL** y *hdc* es **NULL**, crea un contexto de dispositivo para el dispositivo de presentación predeterminado.  
  
 Si *hdc* no **NULL** y `ptd` es **NULL**, la función devuelve existente *hdc*.  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  
   
## <a name="see-also"></a>Vea también  
 [Funciones](../../atl/reference/atl-functions.md)

