---
title: "IUnknown | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IUnknown"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "interfaces COM, base interface"
  - "IUnknown interface"
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# IUnknown
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) es la interfaz base del resto de interfaces COM.  Esta interfaz define tres métodos: [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521), [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) y [Release](http://msdn.microsoft.com/library/windows/desktop/ms682317).  [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) permite a un usuario de la interfaz pedir al objeto un puntero a otras de sus interfaces.  [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) y [Versión](http://msdn.microsoft.com/library/windows/desktop/ms682317) implementan recuento de referencias de la interfaz.  
  
## Vea también  
 [Introducción a COM](../atl/introduction-to-com.md)   
 [IUnknown and Interface Inheritance](http://msdn.microsoft.com/library/windows/desktop/ms692713)