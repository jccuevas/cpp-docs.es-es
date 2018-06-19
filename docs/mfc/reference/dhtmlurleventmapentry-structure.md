---
title: DHtmlUrlEventMapEntry (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DHtmlUrlEventMapEntry
dev_langs:
- C++
helpviewer_keywords:
- DHtmlUrlEventMapEntry structure [MFC]
ms.assetid: 43117c1f-1a51-406c-aa2f-fea647080049
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d038fa188ac431f20b0b19ca8ad8bf675943954c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370063"
---
# <a name="dhtmlurleventmapentry-structure"></a>DHtmlUrlEventMapEntry (Estructura)
El `DHtmlUrlEventMapEntry` estructura proporciona compatibilidad con el mapa de dirección URL de varios eventos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct DHtmlUrlEventMapEntry  
{  
LPCTSTR szUrl;  
const DHtmlEventMapEntry *pEventMap;  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
 `szUrl`  
 La dirección URL.  
  
 *pEventMap*  
 El mapa de eventos asociado con la dirección URL.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdhtml.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

