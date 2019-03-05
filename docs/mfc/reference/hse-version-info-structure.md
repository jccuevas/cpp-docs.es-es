---
title: HSE_VERSION_INFO (Estructura)
ms.date: 11/04/2016
f1_keywords:
- HSE_VERSION_INFO
helpviewer_keywords:
- HSE_VERSION_INFO structure [MFC]
ms.assetid: 4837312d-68c8-4d05-9afa-1934d7d49b20
ms.openlocfilehash: 97f34bebae8a486a825d04b23c5a92fbd4aefa42
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267841"
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

*dwExtensionVersion*<br/>
El número de versión de que el servidor ISA.

*lpszExtensionDesc*<br/>
La descripción de texto de la ISA. La implementación predeterminada proporciona el texto de marcador de posición; invalidar `CHttpServer::GetExtensionVersion` para proporcionar su propia descripción.

## <a name="requirements"></a>Requisitos

**Encabezado:** httpext.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)
