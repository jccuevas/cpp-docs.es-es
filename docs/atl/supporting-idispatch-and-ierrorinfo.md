---
title: "Compatibilidad con IDispatch e IErrorInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IErrorInfo"
  - "IDispatch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDispatch (compatibilidad de la clase en ATL)"
  - "IDispatchImpl (clase)"
  - "IErrorInfo (compatibilidad de la clase en ATL)"
  - "ISupportErrorInfoImpl (método)"
ms.assetid: 7db2220f-319d-4ce9-9382-d340019f14f7
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Compatibilidad con IDispatch e IErrorInfo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede utilizar la clase de plantilla [IDispatchImpl](../atl/reference/idispatchimpl-class.md) para proporcionar una implementación predeterminada de la parte de `IDispatch Interface` de cualquier interfaz dual en el objeto.  
  
 Si el objeto utiliza la interfaz de `IErrorInfo` para notificar errores de nuevo al cliente, el objeto debe admitir la interfaz de `ISupportErrorInfo Interface` .  La clase de plantilla [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) proporciona una manera fácil de implementar esto si tiene una sola interfaz que genera errores en el objeto.  
  
## Vea también  
 [Fundamentals of ATL COM Objects](../atl/fundamentals-of-atl-com-objects.md)