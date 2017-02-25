---
title: "Funci&#243;n de devoluci&#243;n de llamada para CDC::EnumObjects | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Callback Function for CDC::EnumObjects"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "funciones de devolución de llamada, para CDC::EnumObjects"
ms.assetid: 380088b1-88a5-4fb4-bbb5-dd9e8386572b
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Funci&#243;n de devoluci&#243;n de llamada para CDC::EnumObjects
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El nombre *de ObjectFunc* es un marcador de posición para el nombre de función aplicación\- proporcionado.  
  
## Sintaxis  
  
```  
  
      int CALLBACK EXPORT ObjectFunc(   
   LPSTR lpszLogObject,   
   LPSTR* lpData    
);  
```  
  
#### Parámetros  
 *lpszLogObject*  
 Señala una estructura de datos de [LOGPEN](../../mfc/reference/logpen-structure.md) o de [LOGBRUSH](../../mfc/reference/logbrush-structure.md) que contiene información sobre los atributos lógicos de objeto.  
  
 `lpData`  
 Los puntos a los datos aplicación\-proporcionados pasados a `EnumObjects` funcionan.  
  
## Valor devuelto  
 La función de devolución de llamada devuelve `int`.  El valor de este retorno es definido por el usuario.  Si la función de devolución de llamada devuelve 0, `EnumObjects` detiene la enumeración pronto.  
  
## Comentarios  
 El nombre real debe ser exportado.  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::EnumObjects](../Topic/CDC::EnumObjects.md)