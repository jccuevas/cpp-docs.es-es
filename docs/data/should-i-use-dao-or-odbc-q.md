---
title: "&#191;Se debe utilizar DAO u ODBC? | Microsoft Docs"
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
  - "DAO [C++], ODBC"
  - "clases de base de datos [C++], DAO"
  - "clases de base de datos [C++], ODBC"
  - "ODBC [C++], frente a DAO"
ms.assetid: 9f67613f-0056-4ece-8c3a-9872e9563d57
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &#191;Se debe utilizar DAO u ODBC?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  A partir de Visual C\+\+ .NET, el entorno y los asistentes de Visual C\+\+ ya no admiten DAO \(aunque las clases DAO están incluidas y todavía puede utilizarlas\).  Microsoft recomienda la utilización de plantillas OLE DB u ODBC para los proyectos nuevos.  Sólo debería utilizar DAO para mantener las aplicaciones existentes.  
  
 ¿Qué conjunto de clases MFC debería utilizar?  Depende de sus necesidades:  
  
-   Utilice las clases ODBC si sólo va a trabajar con orígenes de datos ODBC, especialmente en situaciones cliente\/servidor, en las que las clases ODBC de MFC proporcionan un mejor rendimiento.  
  
-   Utilice las clases DAO si va a trabajar principalmente con bases de datos de Microsoft Jet \(.mdb\) o con otros formatos de base de datos que pueda leer directamente el motor de bases de datos Microsoft Jet.  Para consultar una lista de estas bases de datos, vea [Bases de datos a las que se puede obtener acceso con DAO y ODBC](../data/what-data-sources-can-i-access-with-dao-and-odbc-q.md)  
  
-   Obtenga acceso a orígenes de datos ODBC a través de las clases DAO cuando desee la velocidad del motor de bases de datos Microsoft Jet y la funcionalidad adicional de las clases DAO.  
  
    > [!NOTE]
    >  DAO requiere espacio adicional en el disco duro.  
  
 Las clases DAO ofrecen las siguientes ventajas:  
  
-   Mejor rendimiento en algunos casos, especialmente al utilizar bases de datos de Microsoft Jet \(.mdb\).  
  
-   Compatibilidad con las clases ODBC y con Microsoft Access Basic y Microsoft Visual Basic.  
  
-   Acceso a reglas de validación.  
  
-   Capacidad de especificar relaciones entre tablas.  
  
-   Un modelo de acceso a datos más variado, compatible con el Lenguaje de definición de datos \(DDL\) y con el Lenguaje de manipulación de datos \(DML\).  Para obtener más información, vea [Definición y manipulación de bases de datos](../data/are-ddl-and-dml-supported-q.md).  
  
 La tabla siguiente resume las diferencias clave para ayudarle a elegir.  
  
### Elegir entre clases DAO de MFC y clases ODBC de MFC  
  
|¿Me ofrecen...|... las clases DAO?|...las clases ODBC?|  
|--------------------|-------------------------|-------------------------|  
|Acceso a archivos .MDB|Sí|Sí|  
|Acceso a orígenes de datos ODBC|Sí|Sí|  
|Disponibilidad para 16 bits|No|Sí|  
|Disponibilidad para 32 bits|Sí|Sí|  
|Disponibilidad para 64 bits|No|Sí|  
|Compactación de bases de datos|Sí|No|  
|Compatibilidad con el motor de bases de datos|Motor de bases de datos Microsoft Jet|DBMS de destino|  
|Compatibilidad con DDL|Sí|Sólo a través de llamadas directas a ODBC|  
|Compatibilidad con DML|Sí|Sí|  
|Tipo de implementación de MFC|Un "contenedor" de las funciones básicas de DAO|Una abstracción simplificada en lugar de un "contenedor" de la API de ODBC|  
|Optimización|Para archivos .mdb \(Microsoft Access\)|Para cualquier DBMS para el que tenga un controlador, especialmente en situaciones cliente\/servidor|  
|Compatibilidad con transacciones|Para cada solución o, en el caso de datos ODBC, para cada base de datos|Para cada base de datos|  
  
 Tenga en cuenta que las capacidades de los distintos controladores ODBC varían.  Para obtener más información, vea la *Referencia del programador* de ODBC y el archivo de Ayuda del controlador ODBC.  
  
## Vea también  
 [Preguntas más frecuentes sobre Data Access](../data/data-access-frequently-asked-questions-mfc-data-access.md)