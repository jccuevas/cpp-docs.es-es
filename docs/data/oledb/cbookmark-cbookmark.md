---
title: "CBookmark::CBookmark | Microsoft Docs"
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
  - "CBookmark<0>.CBookmark<0>"
  - "CBookmark::CBookmark"
  - "ATL.CBookmark.CBookmark"
  - "CBookmark.CBookmark"
  - "CBookmark"
  - "ATL::CBookmark<0>::CBookmark<0>"
  - "ATL.CBookmark<0>.CBookmark<0>"
  - "CBookmark<0>::CBookmark<0>"
  - "ATL::CBookmark::CBookmark"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBookmark (clase), constructor"
ms.assetid: 84f4ad2b-67d4-4ba3-8b2b-656a66fb6298
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBookmark::CBookmark
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Constructor.  
  
## Sintaxis  
  
```  
  
      CBookmark( );   
CBookmark(  
   DBLENGTH nSize   
);  
```  
  
#### Parámetros  
 `nSize`  
 \[in\] Tamaño del búfer del marcador en bytes.  
  
## Comentarios  
 La primera función establece el búfer a **nulo** y el tamaño de búfer en 0.  La segunda función establece el tamaño de búfer a `nSize`, y el búfer a una matriz de bytes de los bytes de `nSize` .  
  
> [!NOTE]
>  Esta función solo está disponible en **CBookmark\<0\>**.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CBookmark \(Clase\)](../../data/oledb/cbookmark-class.md)