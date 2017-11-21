---
title: DHtmlUrlEventMapEntry (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DHtmlUrlEventMapEntry
dev_langs: C++
helpviewer_keywords: DHtmlUrlEventMapEntry structure [MFC]
ms.assetid: 43117c1f-1a51-406c-aa2f-fea647080049
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 37e43514c116f93841b1479103a6f29ec708bfa0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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

