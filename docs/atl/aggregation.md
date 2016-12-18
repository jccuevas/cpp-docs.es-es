---
title: "Aggregation | Microsoft Docs"
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
  - "aggregate objects [C++]"
  - "aggregation [C++]"
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Aggregation
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En ocasiones el implementador de un objeto desea aprovechar los servicios proporcionados por otros, objeto preintegrada.  Además, desea que este segundo objeto apareciera como parte nativa del primero.  COM alcanza ambos objetivos con la contención y la agregación.  
  
 La agregación significa que el objeto \(externo\) que contiene crea el objeto \(interno\) contenido como parte del proceso de creación y las interfaces del objeto interno se exponen mediante el externo.  Un objeto puede que poderse agregar o no.  Si es, se debe seguir ciertas reglas para que la agregación funcione correctamente.  
  
 Principalmente, todas las llamadas al método de **IUnknown** en el objeto contenido deben delegar al objeto que contiene.  
  
## Vea también  
 [Introducción a COM](../atl/introduction-to-com.md)   
 [Reusing Objects](http://msdn.microsoft.com/library/windows/desktop/ms678443)