---
title: "Interfaces del objeto de comando | Microsoft Docs"
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
  - "interfaces del objeto de comando [C++]"
  - "objetos de comando [OLE DB]"
  - "OLE DB [C++], interfaces del objeto de comando"
ms.assetid: dacff5ae-252c-4f20-9ad7-4e602cc48536
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Interfaces del objeto de comando
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El objeto de comando utiliza la interfaz `IAccessor` para especificar enlaces de parámetros.  El consumidor llama a `IAccessor::CreateAccessor` y le pasa una matriz de estructuras `DBBINDING`.  `DBBINDING` contiene información acerca de los enlaces de columnas \(por ejemplo, tipo y longitud\).  El proveedor recibe la estructura y determina cómo deben transferirse los datos y si es necesario realizar conversiones.  
  
 La interfaz `ICommandText` proporciona una forma de especificar un comando de texto.  La interfaz `ICommandProperties` controla todas las propiedades del comando.  
  
## Vea también  
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)