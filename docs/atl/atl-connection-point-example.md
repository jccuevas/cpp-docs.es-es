---
title: "ATL Connection Point Example | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "puntos de conexión [C++], ejemplos"
  - "examples [ATL]"
ms.assetid: a49721b7-f308-43de-8868-f662a94bc81a
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL Connection Point Example
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este ejemplo se muestra un objeto que admite [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) como interfaz de salida:  
  
 [!code-cpp[NVC_ATL_Windowing#84](../atl/codesnippet/CPP/atl-connection-point-example_1.h)]  
  
 Al especificar `IPropertyNotifySink` como interfaz de salida, puede utilizar la clase [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) en lugar de `IConnectionPointImpl`.  Por ejemplo:  
  
 [!code-cpp[NVC_ATL_Windowing#85](../atl/codesnippet/CPP/atl-connection-point-example_2.h)]  
  
## Vea también  
 [Puntos de conexión](../atl/atl-connection-points.md)