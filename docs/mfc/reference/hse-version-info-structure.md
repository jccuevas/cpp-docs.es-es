---
title: "HSE_VERSION_INFO (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "HSE_VERSION_INFO"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "HSE_VERSION_INFO (estructura)"
ms.assetid: 4837312d-68c8-4d05-9afa-1934d7d49b20
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# HSE_VERSION_INFO (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta estructura es indicada por el parámetro de `pVer` en la función miembro de `CHttpServer::GetExtensionVersion` .  Proporciona el número de versión de ISA y una descripción de texto de ISA.  
  
## Sintaxis  
  
```  
  
      typedef struct _HSE_VERSION_INFO {  
   DWORD dwExtensionVersion;  
   CHAR lpszExtensionDesc[HSE_MAX_EXT_DLL_NAME_LEN];  
} HSE_VERSION_INFO, *LPHSE_VERSION_INFO;  
```  
  
#### Parámetros  
 *dwExtensionVersion*  
 Número de versión de ISA.  
  
 *lpszExtensionDesc*  
 Descripción de texto de ISA.  La implementación predeterminada proporciona el texto del marcador; reemplazo `CHttpServer::GetExtensionVersion` a proporcionar dispone de la descripción.  
  
## Requisitos  
 **Header:** httpext.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)