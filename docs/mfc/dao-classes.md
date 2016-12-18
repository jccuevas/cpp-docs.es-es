---
title: "Clases de DAO | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DAO [C++], clases"
  - "clases de base de datos [C++], DAO"
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clases de DAO
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Estas clases funcionan con otras clases de aplicación para dar acceso fácil a las bases de datos de \(DAO\) del Objeto de acceso a datos, que utilizan el mismo motor de base de datos que Microsoft Visual Basic y Microsoft Access.  Las clases DAO también pueden tener acceso a una gran variedad de bases de datos para los controladores ODBC \(Open Database Connectivity\) están disponibles.  
  
 Los programas que utilizan las bases de datos de DAO tienen al menos un objeto de `CDaoDatabase` y un objeto de `CDaoRecordset` .  
  
> [!NOTE]
>  A partir de Visual C\+\+ .NET, el entorno y los asistentes de Visual C\+\+ ya no admiten DAO \(aunque las clases DAO están incluidas y todavía puede utilizarlas\).  Microsoft recomienda utilizar ODBC para los nuevos proyectos de MFC.  Sólo debería utilizar DAO para mantener las aplicaciones existentes.  
  
 [CDaoWorkspace](../mfc/reference/cdaoworkspace-class.md)  
 Administra una sesión denominada, protegida mediante contraseña de la base de datos de inicio de sesión a cerrar la sesión.  La mayoría de los programas utilizan el área de trabajo predeterminada.  
  
 [CDaoDatabase](../mfc/reference/cdaodatabase-class.md)  
 Una conexión a una base de datos a través de la cual puede funcionar en los datos.  
  
 [CDaoRecordset](../mfc/reference/cdaorecordset-class.md)  
 Representa un conjunto de registros seleccionados de un origen de datos.  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 Una vista que muestra registros de una base de datos en controles.  
  
 [CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)  
 Representa una definición de consulta, normalmente una guardada en una base de datos.  
  
 [CDaoTableDef](../mfc/reference/cdaotabledef-class.md)  
 Representa la definición almacenada de una tabla base o una tabla asociada.  
  
 [CDaoException](../mfc/reference/cdaoexception-class.md)  
 Representa una condición de excepción que surge de las clases DAO.  
  
 [CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)  
 Admite las rutinas de intercambio de campos del registro \(DFX\) de DAO utilizadas por las clases de base de datos DAO.  No utilizará normalmente directamente esta clase.  
  
## Clases relacionadas  
 [CLongBinary](../mfc/reference/clongbinary-class.md)  
 Encapsula un identificador al almacenamiento para un objeto binario grande \(BLOB\), como un mapa de bits.  los objetos de`CLongBinary` se utilizan para administrar los objetos de datos grandes almacenados en tablas de base de datos.  
  
 [COleCurrency](../mfc/reference/colecurrency-class.md)  
 El contenedor de la automatización OLE escribe **DIVISA**, tipo de punto fijo de la aritmética, con 15 dígitos antes del separador decimal y 4 dígitos después.  
  
 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)  
 Contenedor para el tipo **date**de automatización OLE.  Representa valores de fecha y hora.  
  
 [COleVariant](../mfc/reference/colevariant-class.md)  
 Contenedor para el tipo **VARIANT**de automatización OLE.  Los datos en s para **VARIANT**pueden almacenarse en muchos formatos.  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)