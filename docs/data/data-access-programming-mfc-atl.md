---
title: "Programaci&#243;n del acceso a datos (MFC/ATL) | Microsoft Docs"
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
  - "datos [C++], tecnologías de acceso a datos"
  - "acceso a datos [C++], bibliotecas de clases para bases de datos"
  - "bases de datos [C++], MFC"
  - "MFC [C++], aplicaciones de acceso a datos"
  - "OLE DB [C++], tecnologías de acceso a datos"
ms.assetid: def97b2c-b5a6-445f-afeb-308050fd4852
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# Programaci&#243;n del acceso a datos (MFC/ATL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ proporciona varias maneras de trabajar con bases de datos.  La forma preferida es el uso de una de las bibliotecas de clases como Active Template Library \(ATL\) o Microsoft Foundation Class \(MFC\), que simplifican el trabajo con las API de base de datos.  
  
> [!NOTE]
>  Este tema trata sobre las tecnologías antiguas para la programación con bases de datos en Visual C\+\+.  Para obtener información sobre la programación del acceso a datos mediante Visual C\+\+ y SQL Server 2005, vea [Acceso a datos en ASP.NET \(Visual Studio\)](../dotnet/data-access-using-adonet-cpp-cli.md), [Obtener acceso a los datos en Visual Studio](../Topic/Accessing%20data%20in%20Visual%20Studio.md) y [Creating SQL Server 2005 Objects In Managed Code](http://msdn.microsoft.com/es-es/5358a825-e19b-49aa-8214-674ce5fed1da).  
  
 Las clases de biblioteca admiten los siguientes tipos de acceso a datos:  
  
-   ATL proporciona plantillas OLE DB y atributos de base de datos.  
  
-   MFC proporciona ODBC \(Conectividad abierta de bases de datos\) y un controlador ODBC.  
  
 Estas bibliotecas proporcionan abstracciones que simplifican el trabajo con bases de datos, dotándolo de la velocidad, eficacia y flexibilidad de C\+\+.  Integran el acceso a datos con el marco de trabajo de aplicaciones de la biblioteca.  
  
 Como alternativa, se puede llamar directamente a funciones de API de base de datos de los kits de desarrollo de software \(SDK\) de COM, ODBC o DAO.  Para obtener más información sobre la programación directa con las funciones de API de COM, DAO u ODBC, vea el SDK de COM, el SDK de DAO o el SDK de ODBC.  
  
 Utilice el OLE DB de ATL si necesita tener acceso a datos, independientemente de la forma en la que éstos se almacenan.  Utilice las clases ODBC de MFC cuando no esté utilizando bases de datos de Microsoft Jet \(.mdb\) y desee trabajar con la API de ODBC para disponer de una independencia total del origen de datos.  Utilice las clases DAO de MFC cuando trabaje con bases de datos de Microsoft Jet \(.mdb\), o con bases de datos externas como orígenes de datos ODBC.  
  
> [!NOTE]
>  Microsoft recomienda el uso de OLE DB u ODBC para nuevos proyectos.  Sólo se debe utilizar DAO para mantener las aplicaciones existentes.  
  
 Además de crear aplicaciones independientes de base de datos, también puede utilizar una base de datos en otros tipos de programas, como un medio eficaz de almacenamiento y recuperación de datos.  
  
|Para obtener información adicional acerca de|Vea|  
|--------------------------------------------------|---------|  
|**Seleccionar una tecnología de base de datos**||  
|ODBC frente a  DAO|[¿Se debe utilizar DAO u ODBC?](../data/should-i-use-dao-or-odbc-q.md)|  
|Utilizar Microsoft Knowledge Base para buscar artículos adicionales sobre temas de bases de datos, redactados por ingenieros de soporte técnico|[Microsoft Knowledge Base](../data/where-can-i-find-microsoft-knowledge-base-articles-on-database-topics-q.md)|  
|**Compatibilidad con bases de datos ATL \(OLE DB\)**||  
|Programación OLE DB \(temas conceptuales\)|[Información general sobre la programación de OLE DB](../data/oledb/ole-db-programming-overview.md)|  
|Utilizar las plantillas de consumidor OLE DB \(temas conceptuales\)|[Plantillas de consumidor OLE DB](../data/oledb/ole-db-consumer-templates-cpp.md)|  
|Atributos de consumidor OLE DB|[Atributos del consumidor OLE DB](../windows/ole-db-consumer-attributes.md)|  
|Utilizar las plantillas de proveedor OLE DB \(temas conceptuales\)|[Plantillas de proveedores OLE DB](../data/oledb/ole-db-provider-templates-cpp.md)|  
|Agregar un consumidor OLE DB a un proyecto MFC|[Crear un consumidor OLE DB](../data/oledb/creating-an-ole-db-consumer.md)|  
|**Compatibilidad con bases de datos MFC \(ODBC y DAO\)**||  
|En qué consiste DAO y ODBC|[¿Qué son DAO y ODBC?](../data/what-are-dao-and-odbc-q.md)|  
|Cuándo utilizar las clases de base de datos MFC|[¿Cuándo se deben utilizar las clases de base de datos?](../data/when-should-i-use-the-database-classes-q.md)|  
|Aprender acerca del modelo de programación de bases de datos de MFC|[¿Qué es el modelo de programación de base de datos de MFC?](../data/what-is-the-mfc-database-programming-model-q.md)|  
|Elegir entre las clases DAO de MFC y las clases ODBC de MFC|[¿Se debe utilizar DAO u ODBC?](../data/should-i-use-dao-or-odbc-q.md)|  
|Orígenes de datos a los que se puede obtener acceso con DAO y ODBC|[Orígenes de datos a los que se puede obtener acceso con DAO y ODBC](../data/what-data-sources-can-i-access-with-dao-and-odbc-q.md)|  
|Conectividad abierta de bases de datos \(ODBC\)|[ODBC y MFC](../data/odbc/odbc-and-mfc.md)|  
|Saber si se puede llamar directamente a las API de DAO o de ODBC mientras se utilizan las clases|[¿Se puede llamar directamente a objetos DAO u ODBC?](../data/can-i-call-dao-or-odbc-directly-q.md)|  
|Controladores ODBC disponibles|[Lista de controladores ODBC](../data/odbc/odbc-driver-list.md)|  
|Cómo funcionan las clases de base de datos con la arquitectura documento\/vista de MFC|[MFC: Utilizar clases de base de datos con documentos y vistas](../data/mfc-using-database-classes-with-documents-and-views.md)|  
|Configurar la compatibilidad con bases de datos de MFC; conocer qué controladores ODBC se instalan de forma predeterminada en Visual C\+\+, y qué componentes de los SDK de ODBC y DAO se instalan|[Configurar compatibilidad con bases de datos MFC](../data/installing-mfc-database-support.md)|  
|**Controles enlazados a datos \(ADO y RDO\)**||  
|Crear un programa que utiliza controles enlazados a datos|[Controles enlazados a datos \(ADO y RDO\)](../data/ado-rdo/data-bound-controls-ado-and-rdo.md)|  
|Enlace de datos con controles ActiveX|[Controles ActiveX de MFC: utilizar enlace de datos en un control ActiveX](../mfc/mfc-activex-controls-using-data-binding-in-an-activex-control.md)|  
|Distribuir controles ActiveX|[Controles ActiveX de MFC: distribuir controles ActiveX](../mfc/mfc-activex-controls-distributing-activex-controls.md)|  
  
## Vea también  
 [Acceso a datos en ASP.NET \(Visual Studio\)](../Topic/Data%20Access%20in%20Visual%20C++.md)