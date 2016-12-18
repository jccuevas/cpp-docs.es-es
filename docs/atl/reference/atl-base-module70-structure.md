---
title: "_ATL_BASE_MODULE70 Structure | Microsoft Docs"
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
  - "ATL::_ATL_BASE_MODULE70"
  - "ATL._ATL_BASE_MODULE70"
  - "_ATL_BASE_MODULE70"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ATL_BASE_MODULE70 structure"
  - "ATL_BASE_MODULE70 structure"
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
caps.latest.revision: 15
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _ATL_BASE_MODULE70 Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Utilizado por cualquier proyecto que utilice ATL.  
  
## Sintaxis  
  
```  
  
      struct _ATL_BASE_MODULE70{  
   UINT cbSize;  
   HINSTANCE m_hInst;  
   HINSTANCE m_hInstResource;  
   bool m_bNT5orWin98;  
   DWORD dwAtlBuildVer;  
   GUID* pguidVer;  
   CRITICAL_SECTION m_csResource;  
   CSimpleArray<HINSTANCE> m_rgResourceInstance;  
};  
```  
  
## Members  
 `cbSize`  
 El tamaño de la estructura, utilizado para la versión.  
  
 `m_hInst`  
 **hInstance** para este módulo \(EXE o DLL\).  
  
 `m_hInstResource`  
 Identificador de recursos predeterminado de la instancia.  
  
 **m\_bNT5orWin98**  
 Información de versión del sistema operativo.  Se utiliza internamente para ATL.  
  
 **dwAtlBuildVer**  
 Almacena la versión ATL.  Actualmente 0x0700.  
  
 **pguidVer**  
 GUID interno de ATL.  
  
 **m\_csResource**  
 Se utiliza para sincronizar el acceso a la matriz de **m\_rgResourceInstance** .  Se utiliza internamente para ATL.  
  
 **m\_rgResourceInstance**  
 La matriz se usa para buscar los recursos en todo el recurso cita como ejemplo cuyo ATL reconoce.  Se utiliza internamente para ATL.  
  
## Comentarios  
 [\_ATL\_BASE\_MODULE](../Topic/_ATL_BASE_MODULE.md) se define como typedef de `_ATL_BASE_MODULE70`.  
  
## Requisitos  
 **encabezado:** atlcore.h  
  
## Vea también  
 [Estructuras](../../atl/reference/atl-structures.md)