---
title: "_ATL_MODULE70 Structure | Microsoft Docs"
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
  - "_ATL_MODULE70"
  - "ATL::_ATL_MODULE70"
  - "ATL._ATL_MODULE70"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ATL_MODULE70 structure"
  - "ATL_MODULE70 structure"
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
caps.latest.revision: 16
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _ATL_MODULE70 Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Contiene los datos utilizados por cada agente de ATL.  
  
## Sintaxis  
  
```  
  
      struct _ATL_MODULE70{  
   UINT cbSize;  
   LONG m_nLockCnt;  
   _ATL_TERMFUNC_ELEM* m_pTermFuncs;  
   CComCriticalSection m_csStaticDataInitAndTypeInfo;  
};  
```  
  
## Members  
 `cbSize`  
 El tamaño de la estructura, utilizado para la versión.  
  
 `m_nLockCnt`  
 Haga referencia al número para determinar cuánto tiempo el módulo debe permanecer activo.  
  
 **m\_pTermFuncs**  
 Siga las funciones registrados para llamar cuando ATL se cierra.  
  
 **m\_csStaticDataInitAndTypeInfo**  
 Se utiliza para coordinar el acceso a los datos internos en escenarios multiproceso.  
  
## Comentarios  
 [\_ATL\_MODULE](../Topic/_ATL_MODULE.md) se define como typedef de `_ATL_MODULE70`.  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [Estructuras](../../atl/reference/atl-structures.md)