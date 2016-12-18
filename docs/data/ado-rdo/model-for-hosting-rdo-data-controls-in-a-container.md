---
title: "Modelo para alojar controles de datos de RDO en un contenedor | Microsoft Docs"
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
  - "RemoteData (control de RDO), modelo para alojamiento"
  - "RemoteData (control), modelo para alojamiento"
ms.assetid: ca598bac-9fef-40e6-b6cd-03d817e16b2e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Modelo para alojar controles de datos de RDO en un contenedor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un contenedor hospeda un control de datos de RDO de la manera siguiente:  
  
-   El contenedor obtiene una interfaz IVBDSC del control de datos.  Si no puede encontrar IVBDSC, no es un control de datos.  
  
-   Después, el contenedor obtiene la interfaz **ICursor** del control de datos.  Estas interfaces proporcionan un objeto Cursor que pueden manipular los clientes.  
  
-   Por último, el contenedor enlaza con la interfaz **INotifyDBEvents** del control de datos.  Esta interfaz permite al contenedor recibir notificaciones desde el control de datos.  Para ello, éste debe ser compatible con la interfaz **INotifyDBEventsSink**.  
  
 Un contenedor hospeda un control enlazado a datos de RDO de la manera siguiente:  
  
-   El control admite la interfaz **IBoundObject** y el contenedor admite la interfaz **IBoundObjectSite**.  El control obtiene la interfaz **IBoundObjectSite** del contenedor y el contenedor obtiene la interfaz **IBoundObject** del control.  
  
-   El control admite la interfaz **IPropNotifySink** y enlaza con el contenedor.  Esto permite al contenedor recibir notificaciones desde el control.  
  
-   Si el control admite **INotifyDBEventsSink**, puede recibir notificaciones desde un control de datos de RDO después de conectar con la interfaz **INotifyDBEvents** del control de datos.  
  
-   El control podrá recibir objetos cursor desde el control de datos \(directamente o a través del contenedor\).  Es posible manipular y desplazar los cursores.  En este punto, se habrá enlazado correctamente el control enlazado a datos de RDO.  
  
## Vea también  
 [Enlace de datos de RDO](../../data/ado-rdo/rdo-databinding.md)   
 [Utilizar el enlace de datos de RDO en Visual C\+\+](../../data/ado-rdo/using-rdo-databinding-in-visual-cpp.md)