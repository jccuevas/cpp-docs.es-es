---
title: "Mejorar un proveedor sencillo de s&#243;lo lectura | Microsoft Docs"
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
  - "IRowsetLocate (clase)"
  - "IRowsetLocate (clase), agregar a proveedores de plantillas OLE DB"
  - "proveedor de sólo lectura [C++]"
  - "proveedores de sólo lectura simples [C++]"
ms.assetid: cba0e09f-44c1-41c1-9456-332aa13dc158
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Mejorar un proveedor sencillo de s&#243;lo lectura
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En esta sección se muestra cómo mejorar el [proveedor sencillo de solo lectura](../../data/oledb/implementing-the-simple-read-only-provider.md) creado en la sección anterior.  `IRowsetLocateImpl` crea una implementación de la interfaz `IRowsetLocate` y agrega automáticamente compatibilidad con marcadores.  
  
 Cuando tenga un proveedor en funcionamiento, es posible que desee mejorarlo para implementar la actualización del proveedor, controlar transacciones o mejorar el rendimiento del algoritmo de búsqueda en filas.  La mayoría de las mejorías del proveedor implican agregar una interfaz a un objeto COM existente.  
  
 En el ejemplo de los temas siguientes se mejora el mecanismo de búsqueda en filas agregando la interfaz `IRowsetLocate` a `CAgentRowset`.  En estos temas se muestra la forma de:  
  
-   [Hacer que RMyProviderRowset herede de IRowsetLocate](../../data/oledb/modifying-the-inheritance-of-rmyproviderrowset.md).  
  
-   [Determinar dinámicamente las columnas que se devuelven al consumidor](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).  
  
## Vea también  
 [Crear un proveedor sencillo de sólo lectura](../../data/oledb/creating-a-simple-read-only-provider.md)