---
title: HSE_VERSION_INFO (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- HSE_VERSION_INFO
dev_langs:
- C++
helpviewer_keywords:
- HSE_VERSION_INFO structure [MFC]
ms.assetid: 4837312d-68c8-4d05-9afa-1934d7d49b20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: daf1565c2fe2d7a4620f83b765671fea80502102
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335820"
---
# <a name="hseversioninfo-structure"></a>HSE_VERSION_INFO (Estructura)
Esta estructura se apunta la *pVer* parámetro en el `CHttpServer::GetExtensionVersion` función miembro. Proporciona el número de versión ISA y una descripción textual de la ISA.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct _HSE_VERSION_INFO {  
    DWORD dwExtensionVersion;  
    CHAR lpszExtensionDesc[HSE_MAX_EXT_DLL_NAME_LEN];  
} HSE_VERSION_INFO, *LPHSE_VERSION_INFO;  
```  
  
#### <a name="parameters"></a>Parámetros  
 *dwExtensionVersion*  
 El número de versión de que el servidor ISA.  
  
 *lpszExtensionDesc*  
 La descripción de texto de la ISA. La implementación predeterminada proporciona el texto de marcador de posición; invalidar `CHttpServer::GetExtensionVersion` para proporcionar su propia descripción.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** httpext.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

