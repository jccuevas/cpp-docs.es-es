---
title: "Probar un proveedor | Microsoft Docs"
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
  - "proveedores OLE DB, pruebas"
  - "probar proveedores"
  - "pruebas, proveedores OLE DB"
ms.assetid: bf824fe4-81af-4ffb-beb3-4fa2928dc450
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Probar un proveedor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Antes de liberar un proveedor deberá realizar las pruebas siguientes, en el orden indicado.  Estas pruebas garantizan que el proveedor funciona correctamente para la mayoría de los posibles usuarios.  
  
1.  Pruebe el proveedor mediante una aplicación [consumidor](../../data/oledb/creating-an-ole-db-consumer.md) programada con las plantillas de consumidor OLE DB.  El consumidor de prueba debe cubrir todas las áreas funcionales del proveedor \(todo el código que haya agregado o modificado\).  
  
2.  Pruebe el proveedor con una aplicación de consumidor programada con ADO.  La mayoría de los programadores \(especialmente los que utilizan Microsoft Visual Basic y Microsoft C\#\) utilizan ADO o ADO.NET para las aplicaciones de consumidor.  El consumidor de prueba debe cubrir todas las áreas funcionales del proveedor.  Si desea examinar un ejemplo de aplicación de consumidor ADO, vea [Ejemplos de código ADO en Microsoft Visual Basic](https://msdn.microsoft.com/en-us/library/ms807514.aspx).  
  
3.  Ejecute las pruebas de conformidad de OLE DB \(incluidas las pruebas de conformidad de ADO\) para asegurarse de que el proveedor satisface el estándar de nivel 0 para proveedores de OLE DB. \(Para obtener una explicación del nivel 0, busque “nivel 0 Conformance OLE DB test” en [La guía del programador de OLE DB](http://go.microsoft.com/fwlink/?LinkId=121548).  Estas pruebas y la documentación asociada se incluyen en Visual C\+\+, en el SDK de Data Access.  Estas pruebas también le ayudarán a asegurarse de que el proveedor se ejecuta correctamente cuando se agrega a través de otros [proveedores de servicios](../../data/oledb/ole-db-resource-pooling-and-services.md) y son especialmente útiles si modifica o agrega propiedades.  Para obtener más información acerca de las pruebas de conformidad, vea el archivo Léame del SDK de Data Access, que se encuentra en uno de los CD de Visual Studio.  
  
## Vea también  
 [Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)