---
title: TerminateMap (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
dev_langs:
- C++
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d33cbd46903a37bf42e417a100d26c9b706058c0
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645943"
---
# <a name="terminatemap-function"></a>TerminateMap (Función)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
inline bool TerminateMap(  
   _In_ ModuleBase *module,   
   _In_opt_z_ const wchar_t *serverName,   
    bool forceTerminate) throw()  
```  
  
### <a name="parameters"></a>Parámetros  
 *módulo*  
 Un [módulo](../windows/module-class.md).  
  
 *Nombre de servidor*  
 El nombre de un subconjunto de los generadores de clases en el módulo especificado por el parámetro *módulo*.  
  
 *forceTerminate*  
 **True** para terminar la clase generadores independientemente de están activos; **false** no terminar los generadores de clases si cualquier factory está activo.  
  
## <a name="return-value"></a>Valor devuelto  
 **True** si todos los generadores de clases se han finalizado; en caso contrario, **false**.  
  
## <a name="remarks"></a>Comentarios  
 Cierra los generadores de clases en el módulo especificado.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)