---
title: TerminateMap (función) | Documentos de Microsoft
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
ms.openlocfilehash: b4787fec0a6b4b9f55c500b66786372945d9a523
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890354"
---
# <a name="terminatemap-function"></a>TerminateMap (Función)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
inline bool TerminateMap(  
   _In_ ModuleBase *module,   
   _In_opt_z_ const wchar_t *serverName,   
    bool forceTerminate) throw()  
```  
  
## <a name="parameters"></a>Parámetros  
 `module`  
 A [módulo](../windows/module-class.md).  
  
 `serverName`  
 El nombre de un subconjunto de los generadores de clases en el módulo especificado por el parámetro `module`.  
  
 `forceTerminate`  
 `true` para finalizar la clase generadores independientemente de están activos; `false` no terminar los generadores de clases si cualquier generador está activo.  
  
## <a name="return-value"></a>Valor devuelto  
 `true` Si se han terminado todos los generadores de clases; en caso contrario, `false`.  
  
## <a name="remarks"></a>Comentarios  
 Cierra los generadores de clases en el módulo especificado.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)