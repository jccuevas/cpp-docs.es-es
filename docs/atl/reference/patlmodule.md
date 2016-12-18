---
title: "_pAtlModule | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATLBASE/_pAtlModule"
  - "_pAtlModule"
  - "ATL::_pAtlModule"
  - "ATL._pAtlModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_pAtlModule variable"
  - "pAtlModule variable"
ms.assetid: 0ecde3a9-3f4d-4c7b-bb54-713ce05c4777
caps.latest.revision: 13
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _pAtlModule
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una variable global que almacena un puntero al módulo actual.  
  
## Sintaxis  
  
```  
__declspec(selectany) CAtlModule * _pAtlModule  
```  
  
## Comentarios  
 Los métodos de esta variable global se pueden utilizar para proporcionar la funcionalidad que \(ahora\) la clase obsoleto [CComModule](../../atl/reference/ccommodule-class.md) proporcionado en Visual C\+\+ 6,0.  
  
## Ejemplo  
 [!code-cpp[NVC_ATL_Windowing#97](../../atl/codesnippet/CPP/patlmodule_1.cpp)]  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [Global Variables](../../atl/reference/atl-global-variables.md)