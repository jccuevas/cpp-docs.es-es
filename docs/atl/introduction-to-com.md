---
title: "Introducci&#243;n a COM | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "index-page "
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COM"
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Introducci&#243;n a COM
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

COM es “modelo de objetos fundamental” en qué Controles ActiveX y OLE se compilan.  COM permite a un objeto exponer su funcionalidad a otros componentes y aplicaciones host.  Define cómo el objeto se expone y cómo esta exposición funciona a través de procesos y a través de redes.  COM también define el ciclo de vida del objeto.  
  
 El fundamental para COM es estos conceptos:  
  
-   [interfaces](../atl/interfaces-atl.md) — el mecanismo a través del cual un objeto expone su funcionalidad.  
  
-   [IUnknown](../atl/iunknown.md) — la interfaz básica en la que se basan todos los demás.  Implementa el recuento de referencias y la interfaz que vea los mecanismos que se ejecutan con COM.  
  
-   [recuento de referencias](../atl/reference-counting.md) — la técnica por la que un objeto \(o, estrictamente, una interfaz\) decide cuando se utiliza y ya no por consiguiente libre de quitarse.  
  
-   [QueryInterface](../atl/queryinterface.md) — el método utilizado para consultar un objeto para una interfaz determinada.  
  
-   [cálculo de referencias](../atl/marshaling.md) — el mecanismo que permite que los objetos que se utilizarán a través del subproceso, del proceso, y los límites de la red, teniendo en cuenta la independencia de la ubicación.  
  
-   [agregación](../atl/aggregation.md) \(una manera en la que el objeto puede hacer uso de otro.  
  
## Vea también  
 [Introduction to COM and ATL](../atl/introduction-to-com-and-atl.md)   
 [The Component Object Model](http://msdn.microsoft.com/library/windows/desktop/ms694363)