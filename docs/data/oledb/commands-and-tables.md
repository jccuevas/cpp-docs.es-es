---
title: "Comandos y tablas | Microsoft Docs"
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
  - "CAccessorRowset (clase), clases de comandos y tablas"
  - "CCommand (clase), plantillas de consumidor OLE DB"
  - "comandos [C++], Plantillas de consumidor OLE DB"
  - "CTable (clase)"
  - "plantillas de consumidor OLE DB, compatibilidad con comandos"
  - "plantillas de consumidor OLE DB, compatibilidad con tablas"
  - "conjuntos de filas, obtener acceso"
  - "tablas [C++], Plantillas de consumidor OLE DB"
ms.assetid: 4bd3787b-6d26-40a9-be0c-083080537c12
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Comandos y tablas
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Los comandos y tablas permiten el acceso a los conjuntos de filas; es decir, abrir los conjuntos de filas, ejecutar comandos y enlazar columnas.  Las clases [CCommand](../../data/oledb/ccommand-class.md) y [CTable](../../data/oledb/ctable-class.md) crean instancias de los objetos de comando y tabla, respectivamente.  Estas clases se derivan de [CAccessorRowset](../../data/oledb/caccessorrowset-class.md), como se muestra en la ilustración siguiente.  
  
 ![CCommand y CTable](../../data/oledb/media/vccommandstables.png "vcCommandsTables")  
Clases de comando y tabla  
  
 En la tabla anterior, `TAccessor` puede ser cualquier tipo de descriptor de acceso incluido en [Tipos de descriptores de acceso](../../data/oledb/accessors-and-rowsets.md).  *TRowset* puede ser cualquier tipo de conjunto de filas incluido en [Tipos de conjuntos de filas](../../data/oledb/accessors-and-rowsets.md).  *TMultiple* especifica el tipo de resultados \(uno o varios conjuntos de resultados\).  
  
 El [Asistente para consumidores OLE DB ATL](../../atl/reference/atl-ole-db-consumer-wizard.md) permite especificar si se desea un objeto de comando o tabla.  
  
-   Para orígenes de datos sin comandos, se puede utilizar en su lugar la clase `CTable`.  Normalmente se utiliza para conjuntos de filas simples que no especifican parámetros y no requieren múltiples resultados.  Esta clase abre una tabla de un origen de datos usando un nombre de tabla especificado por el programador.  
  
-   Para orígenes de datos que admiten el uso de comandos, se puede utilizar en su lugar la clase `CCommand`.  Para ejecutar un comando, llame a [Open](../../data/oledb/ccommand-open.md) en esta clase.  Como alternativa, se puede llamar a `Prepare` para preparar un comando que se desee ejecutar más de una vez.  
  
     **CCommand** tiene tres argumentos de plantilla: un tipo de descriptor de acceso, un tipo de conjunto de filas y un tipo de resultados \(`CNoMultipleResults`, de forma predeterminada, o `CMultipleResults`\).  Si se especifica `CMultipleResults`, la clase `CCommand` admite la interfaz **IMultipleResults** y controla múltiples conjuntos de filas.  En el ejemplo [DBVIEWER](http://msdn.microsoft.com/es-es/07620f99-c347-4d09-9ebc-2459e8049832) se muestra cómo controlar múltiples resultados.  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)