---
title: "Marshaling | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "interfaces COM, calcular las referencias"
  - "calcular las referencias"
  - "calcular las referencias, interoperabilidad COM"
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Marshaling
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La técnica COM de cálculo de referencias permite las interfaces expuestas por un objeto en un proceso que se utilizará en otro proceso.  En cálculo de referencias, COM proporciona el código \(o el código de las aplicaciones proporcionado por el implementador de la interfaz\) tanto para empaquetar los parámetros de un método en un formato que puede desplazarse entre procesos \(así como, a través de la conexión a los procesos que se ejecutan en otros equipos\) y desempaquetar los parámetros en el otro extremo.  Igualmente, COM debe realizar estos mismos pasos en la devolución de llamada.  
  
> [!NOTE]
>  El cálculo de referencias no suele ser necesario cuando una interfaz proporcionada por un objeto se utiliza en el mismo proceso que el objeto.  Sin embargo, el cálculo de referencias puede ser necesario entre subprocesos.  
  
## Vea también  
 [Introducción a COM](../atl/introduction-to-com.md)   
 [Marshaling Details](http://msdn.microsoft.com/library/windows/desktop/ms692621)