---
title: "Convertir datos no compatibles con el proveedor | Microsoft Docs"
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
  - "plantillas del proveedor OLE DB, tipos de datos no admitidos"
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Convertir datos no compatibles con el proveedor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cuando el consumidor solicita un tipo de datos que no admite el proveedor, el código de la plantilla de proveedor OLE DB para `IRowsetImpl::GetData` llama a Msdadc.dll para convertir el tipo de datos.  
  
 Si implementa una interfaz como `IRowsetChange` que requiera la conversión de datos, puede llamar a Msdaenum.dll para realizar la conversión.  Utilice la función `GetData`, definida en Atldb.h, por ejemplo.  
  
## Vea también  
 [Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)