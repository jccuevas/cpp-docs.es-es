---
title: "DHtmlUrlEventMapEntry (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DHtmlUrlEventMapEntry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DHtmlUrlEventMapEntry (estructura)"
ms.assetid: 43117c1f-1a51-406c-aa2f-fea647080049
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DHtmlUrlEventMapEntry (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `DHtmlUrlEventMapEntry` proporciona compatibilidad de mapa de eventos de la multi\- dirección URL.  
  
## Sintaxis  
  
```  
  
      struct DHtmlUrlEventMapEntry  
{  
   LPCTSTR szUrl;  
   const DHtmlEventMapEntry *pEventMap;  
};  
```  
  
#### Parámetros  
 `szUrl`  
 La dirección URL.  
  
 *pEventMap*  
 El mapa de evento asociado a la dirección URL.  
  
## Requisitos  
 **Header:** afxdhtml.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)