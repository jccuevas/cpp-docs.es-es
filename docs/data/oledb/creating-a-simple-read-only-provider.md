---
title: "Crear un proveedor sencillo de s&#243;lo lectura | Microsoft Docs"
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
  - "plantillas del proveedor OLE DB, crear proveedores"
  - "proveedores OLE DB, crear"
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Crear un proveedor sencillo de s&#243;lo lectura
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cuando haya creado un proveedor OLE DB mediante el Asistente para proyectos ATL y el Asistente para proveedores OLE DB ATL, puede agregarle más funcionalidad para la que desee ofrecer compatibilidad.  Cuando empiece a diseñar el proveedor, examine el tipo de datos que va a enviar al consumidor y las condiciones en que va a hacerlo.  Es muy importante determinar si se va a necesitar compatibilidad con comandos, transacciones y otros objetos opcionales.  Un buen diseño inicial acelerará la implementación y las pruebas.  
  
 El ejemplo se presenta en dos partes:  
  
-   En la primera parte se muestra la forma de [crear un proveedor sencillo de sólo lectura](../../data/oledb/implementing-the-simple-read-only-provider.md) que lea un par de cadenas.  
  
-   En la segunda parte se muestra la forma de [mejorar el proveedor sencillo de sólo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md) agregando la interfaz `IRowsetLocate`.  
  
## Vea también  
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)