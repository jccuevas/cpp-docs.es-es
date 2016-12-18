---
title: "Interfaces (ATL) | Microsoft Docs"
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
  - "interfaces COM"
  - "interfaces, COM"
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Interfaces (ATL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una interfaz es la manera en que un objeto expone su funcionalidad al mundo exterior.  En COM, una interfaz es una tabla de punteros \(como C\+\+. vtable\) a las funciones implementadas por el objeto.  La tabla representa la interfaz, y las funciones que se señalan son métodos de la interfaz.  Un objeto puede exponer tantas interfaces mientras que elija.  
  
 Cada interfaz se basa en la interfaz COM fundamentalmente, [IUnknown](../atl/iunknown.md).  Los métodos de **IUnknown** permiten navegar a otras interfaces expuestas por el objeto.  
  
 Además, cada interfaz se asigna un identificador único de interfaz \(IID\).  Esta exclusividad facilita admitir versión de interfaz.  Una nueva versión de una interfaz es simplemente una nueva interfaz, con un nuevo identificador IID.  
  
> [!NOTE]
>  Los identificadores IID para COM estándar y las interfaces VIEJAS están predefinidas.  
  
## Vea también  
 [Introducción a COM](../atl/introduction-to-com.md)   
 [COM Objects and Interfaces](http://msdn.microsoft.com/library/windows/desktop/ms690343)