---
title: "Servicios y agrupaci&#243;n de recursos OLE DB | Microsoft Docs"
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
  - "proveedores OLE DB, agrupación de recursos"
  - "servicios OLE DB [OLE DB]"
  - "servicios OLE DB [OLE DB], requisitos del proveedor"
  - "OLE DB, agrupación de recursos"
  - "agrupación de recursos [OLE DB], requisitos del proveedor"
  - "proveedores de servicios [OLE DB]"
ms.assetid: 360c36e2-25ae-4caf-8ee7-d4a6b6898f68
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Servicios y agrupaci&#243;n de recursos OLE DB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Para trabajar bien con la agrupación de OLE DB, el proveedor debe admitir la agregación de todos los objetos.  Esto es un requisito de cualquier proveedor de OLE DB 1.5 o posterior.  Es fundamental para aprovechar los servicios.  No es posible agrupar los proveedores que no admiten la agregación y no se proporcionan servicios adicionales.  
  
 Para agrupar los proveedores, éstos deben ser compatibles con el modelo de subprocesos libre.  El grupo de recursos determina el modelo de subproceso del proveedor de acuerdo con la propiedad **DBPROP\_THREADMODEL**.  
  
 Si el proveedor tiene un estado de conexión global que puede cambiar mientras el origen de datos está en un estado inicializado, debe admitir la nueva propiedad **DBPROP\_RESETDATASOURCE**.  Se llama a esta propiedad antes de reutilizar una conexión; ofrece al proveedor la oportunidad de limpiar el estado antes de utilizarla otra vez.  Si el proveedor no puede limpiar algún estado asociado a la conexión, puede devolver **DBPROPSTATUS\_NOTSETTABLE** para la propiedad y no se reutilizará la conexión.  
  
 Los proveedores que se conectan a una base de datos remota y pueden detectar si se ha perdido una conexión deben ser compatibles con la propiedad **DBPROP\_CONNECTIONSTATUS**.  Esta propiedad proporciona a los servicios OLE DB la capacidad de detectar conexiones inactivas y asegurarse de que no se devuelvan al grupo.  
  
 Por último, el alistamiento automático de transacciones no se utiliza en general, a menos que se implemente al mismo nivel en el que se produce la agrupación.  Los proveedores que admiten el alistamiento automático de transacciones deben admitir su deshabilitación mediante la exposición de la propiedad **DBPROP\_INIT\_OLEDBSERVICES** y la deshabilitación del alistamiento si se cancela la selección de **DBPROPVAL\_OS\_TXNENLISTMENT**.  
  
## Vea también  
 [Técnicas avanzadas para proveedores](../../data/oledb/advanced-provider-techniques.md)