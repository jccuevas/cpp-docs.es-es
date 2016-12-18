---
title: "IRowsetImpl::RestartPosition | Microsoft Docs"
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
  - "ATL.IRowsetImpl.RestartPosition"
  - "IRowsetImpl::RestartPosition"
  - "RestartPosition"
  - "ATL::IRowsetImpl::RestartPosition"
  - "IRowsetImpl.RestartPosition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RestartPosition (método)"
ms.assetid: 14de66ef-8d2c-4404-adb6-3f6c74ac6cf1
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetImpl::RestartPosition
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Coloca la búsqueda de nuevo siguiente colocar a su posición inicial; es decir, su posición cuando se creó el conjunto de filas primero.  
  
## Sintaxis  
  
```  
  
      STDMETHOD( RestartPosition )(  
   HCHAPTER /* hReserved */   
);  
```  
  
#### Parámetros  
 Vea [IRowset::RestartPosition](https://msdn.microsoft.com/en-us/library/ms712877.aspx) en *la referencia del*programador.  
  
## Comentarios  
 La posición del conjunto de filas es una variable que se denomina **GetNextRow** .  Puede desplazarse hacia atrás en un rowet llamando a [RestartPosition](#vcrefirowsetimplrestartposition) y después capturandolo o moverse hacia atrás.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IRowsetImpl \(Clase\)](../../data/oledb/irowsetimpl-class.md)