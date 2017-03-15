---
title: "Secuencia de operaciones para crear aplicaciones de base de datos | Microsoft Docs"
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
  - "aplicaciones [MFC], base de datos"
  - "aplicaciones de base de datos [C++]"
  - "aplicaciones de base de datos [C++], crear"
  - "MFC [C++], aplicaciones de base de datos"
ms.assetid: 9371da59-8536-43cd-8314-706ad320e2ec
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Secuencia de operaciones para crear aplicaciones de base de datos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La tabla siguiente muestra el rol y el rol de marco en aplicaciones de base de datos de escritura.  
  
> [!NOTE]
>  A partir de Visual C\+\+ .NET, el entorno y los asistentes de Visual C\+\+ ya no admiten DAO \(aunque las clases DAO están incluidas y todavía puede utilizarlas\).  Microsoft recomienda utilizar ODBC para los nuevos proyectos de MFC.  Sólo debería utilizar DAO para mantener las aplicaciones existentes.  
  
### Crear aplicaciones de base de datos  
  
|Tarea|Hace|Hace el marco|  
|-----------|----------|-------------------|  
|Decida si utilizar las clases ODBC de MFC o DAO.|Utilizar ODBC para los nuevos proyectos de MFC.  Utilizar DAO para mantener sólo las existentes.  Vea [¿Se debe utilizar DAO u ODBC?](../data/should-i-use-dao-or-odbc-q.md).  Para obtener información general, vea el artículo [Programación de acceso a datos](../data/data-access-programming-mfc-atl.md).|Las clases de fuentes del marco de trabajo de acceso a bases de datos compatibles con.|  
|Cree la aplicación esqueleto con opciones de base de datos.|Ejecute el asistente para aplicaciones MFC.  Seleccione opciones de la página de compatibilidad con bases de datos.  Si elige una opción que crea una vista de registros, especificar:<br /><br /> -   Origen de datos y nombre de tabla o nombres<br />-   Nombre o nombres de la consulta.|El asistente para aplicaciones MFC crea archivos y especifica el necesario incluye.  Dependiendo de las opciones que especifique, archivos puede incluir una clase de conjunto de registros.|  
|Diseñar el formulario de base de datos o formularios.|Utilice el editor de cuadros de diálogo de Visual C\+\+ para colocar los controles en las clases de vista de los recursos de plantilla de cuadro de diálogo del registro.|El asistente para aplicaciones MFC crea un recurso vacío de plantilla de cuadro de diálogo para completar.|  
|Crear clases de la vista y de conjunto de registros del registro adicional según sea necesario.|Utilice la vista de clases para crear las clases y el editor de cuadros de diálogo para diseñar vistas.|La vista de clases crea archivos adicionales para las nuevas clases.|  
|Cree los objetos de conjunto de registros necesarios en el código.  Utilice los conjuntos de registros para manipular…|Basan conjuntos de registros en las clases derivadas de [CRecordset](../mfc/reference/crecordset-class.md) con los asistentes.|ODBC utiliza el intercambio de campos de registros \(RFX\) para intercambiar datos entre la base de datos y los miembros de datos de campo de conjunto de registros.  Si usa una vista de registros, datos de intercambios de intercambio de datos de diálogo \(DDX\) entre el conjunto de registros y los controles de la vista de registros.|  
|… o cree [CDatabase](../mfc/reference/cdatabase-class.md) explícito en el código de cada base de datos que desea abrir.|Base los objetos de conjunto de registros en los objetos de base de datos.|El objeto de base de datos proporciona una interfaz al origen de datos.|  
|Columnas de datos de enlace al conjunto de registros dinámicamente.|En ODBC, agréguelo a la clase derivada de conjunto de registros para administrar el enlace.  Vea el artículo [Conjunto de registros: Enlazar dinámicamente columnas de datos \(ODBC\)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||  
  
## Vea también  
 [Compilar en el marco](../mfc/building-on-the-framework.md)   
 [Secuencia de operaciones para compilar aplicaciones MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [Secuencia de operaciones para crear aplicaciones OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [Secuencia de operaciones para crear controles ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)