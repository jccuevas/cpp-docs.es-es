---
title: "Utilizar descriptores de acceso manuales | Microsoft Docs"
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
  - "descriptores de acceso [C++], manuales"
  - "control de comandos, plantillas OLE DB"
  - "descriptores de acceso manuales"
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Utilizar descriptores de acceso manuales
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cuando se controla un comando desconocido, deben efectuarse cuatro acciones:  
  
-   Determinar los parámetros  
  
-   Ejecutar el comando  
  
-   Determinar las columnas de resultados  
  
-   Comprobar si existen varios conjuntos de filas de resultados  
  
 Para realizar estas tareas con las plantillas de consumidor OLE DB, use la clase `CManualAccessor` y siga estos pasos:  
  
1.  Abra un objeto `CCommand` con `CManualAccessor` como parámetro de plantilla.  
  
    ```  
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;  
    ```  
  
2.  Vea la sesión de la interfaz **IDBSchemaRowset** y use el conjunto de filas de parámetros del procedimiento.  Si la interfaz **IDBSchemaRowset** no está disponible, haga una consulta acerca de la interfaz `ICommandWithParameters`.  Llame a `GetParameterInfo` para obtener información.  Si no hay interfaces disponibles, se puede suponer que no hay parámetros.  
  
3.  Por cada parámetro, llame a `AddParameterEntry` para agregar los parámetros y establecerlos.  
  
4.  Abra el conjunto de filas, estableciendo el parámetro de enlace en **false**.  
  
5.  Llame a `GetColumnInfo` para recuperar las columnas de resultados.  Use `AddBindEntry` para agregar la columna de resultados al enlace.  
  
6.  Llame a `GetNextResult` para determinar si hay más conjuntos de filas disponibles.  Repita los pasos 2 a 5.  
  
 Para obtener un ejemplo de un descriptor de acceso manual, vea **CDBListView::CallProcedure** en el ejemplo [DBVIEWER](http://msdn.microsoft.com/es-es/07620f99-c347-4d09-9ebc-2459e8049832).  
  
## Vea también  
 [Utilizar descriptores de acceso](../../data/oledb/using-accessors.md)