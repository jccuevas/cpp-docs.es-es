---
title: "Habilitar y deshabilitar servicios para un proveedor | Microsoft Docs"
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
  - "servicios OLE DB [OLE DB], habilitar y deshabilitar"
  - "proveedores de servicios [OLE DB]"
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Habilitar y deshabilitar servicios para un proveedor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Los servicios OLE DB individuales pueden estar habilitados o deshabilitados de manera predeterminada para todas las aplicaciones que tengan acceso a un solo proveedor.  Para ello hay que agregar una entrada de Registro **OLEDB\_SERVICES** bajo el CLSID del proveedor, con un valor `DWORD` que especifique los servicios que hay que habilitar o deshabilitar, como se muestra en la tabla siguiente:  
  
|Servicios predeterminados habilitados|Valor de palabra clave|  
|-------------------------------------------|----------------------------|  
|Todos los servicios \(predeterminado\)|0xffffffff|  
|Todos los servicios excepto Pooling y AutoEnlistment|0xfffffffe|  
|Todos los servicios excepto Client Cursor|0xfffffffb|  
|Todos los servicios, excepto Pooling, AutoEnlistment y Client Cursor|0xfffffff0|  
|Ningún servicio|0x00000000|  
|No hay agregación, todos los servicios deshabilitados|\<clave que faltan\>|  
  
## Vea también  
 [Habilitar y deshabilitar servicios OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)