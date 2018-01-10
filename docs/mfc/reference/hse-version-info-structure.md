---
title: HSE_VERSION_INFO (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: HSE_VERSION_INFO
dev_langs: C++
helpviewer_keywords: HSE_VERSION_INFO structure [MFC]
ms.assetid: 4837312d-68c8-4d05-9afa-1934d7d49b20
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 108f826ffaa17de65dafe246ab6724fac2b134f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="hseversioninfo-structure"></a>HSE_VERSION_INFO (Estructura)
Esta estructura apunta a la `pVer` parámetro en el `CHttpServer::GetExtensionVersion` función miembro. Proporciona el número de versión ISA y una descripción textual de la ISA.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct _HSE_VERSION_INFO {  
    DWORD dwExtensionVersion;  
    CHAR lpszExtensionDesc[HSE_MAX_EXT_DLL_NAME_LEN];  
} HSE_VERSION_INFO, *LPHSE_VERSION_INFO;  
```  
  
#### <a name="parameters"></a>Parámetros  
 *dwExtensionVersion*  
 El número de versión de la ISA.  
  
 *lpszExtensionDesc*  
 La descripción de texto de la ISA. La implementación predeterminada proporciona texto de marcador de posición; invalidar `CHttpServer::GetExtensionVersion` para proporcionar su propia descripción.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** httpext.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

