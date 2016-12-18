---
title: "CBookmark::SetBookmark | Microsoft Docs"
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
  - "CBookmark<0>::SetBookmark"
  - "ATL.CBookmark<0>.SetBookmark"
  - "CBookmark<0>.SetBookmark"
  - "SetBookmark"
  - "ATL::CBookmark::SetBookmark"
  - "ATL::CBookmark<0>::SetBookmark"
  - "CBookmark.SetBookmark"
  - "ATL.CBookmark.SetBookmark"
  - "CBookmark::SetBookmark"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetBookmark (método)"
ms.assetid: bcd26831-6045-4e69-96d6-abf8037fc18d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBookmark::SetBookmark
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Copia el valor del marcador al que hace referencia `pBuffer` en el búfer de `CBookmark` y establece el tamaño de búfer a `nSize`.  
  
## Sintaxis  
  
```  
  
      HRESULT SetBookmark(  
   DBLENGTH nSize,  
   BYTE* pBuffer   
) throw( );  
```  
  
#### Parámetros  
 *nSize*  
 \[in\] El tamaño del búfer del marcador.  
  
 `pBuffer`  
 \[in\] Un puntero a la matriz de bytes que contiene el valor del marcador.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Esta función solo está disponible en **CBookmark\<0\>**.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CBookmark \(Clase\)](../../data/oledb/cbookmark-class.md)