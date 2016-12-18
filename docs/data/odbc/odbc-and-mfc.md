---
title: "ODBC y MFC | Microsoft Docs"
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
  - "conexiones [C++], origen de datos"
  - "conexiones [C++], bases de datos"
  - "orígenes de datos [C++], conectar"
  - "conexiones de bases de datos [C++], clases ODBC de MFC"
  - "bases de datos [C++], conectar"
  - "MFC [C++], ODBC y"
  - "ODBC [C++], MFC"
ms.assetid: 98f02fd7-1235-437b-89a9-edfd0fc797f7
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ODBC y MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  Para utilizar las clases de base de datos MFC en una plataforma Win32 \(como Windows NT\), es necesario disponer de un controlador ODBC adecuado para el origen de datos.  Algunos controladores vienen incluidos en Visual C\+\+; otros se pueden obtener de Microsoft y otros proveedores.  Para obtener información, vea [Lista de controladores ODBC](../../data/odbc/odbc-driver-list.md).  
  
 Este tema presenta los principales conceptos de las clases de base de datos basadas en ODBC de la biblioteca MFC y proporciona información general sobre cómo funcionan las clases entre sí.  Para obtener más información sobre ODBC y MFC, vea los temas siguientes:  
  
-   [Conectarse a un origen de datos](../../data/odbc/connecting-to-a-data-source.md)  
  
-   [Seleccionar y manipular registros](../../data/odbc/selecting-and-manipulating-records.md)  
  
-   [Mostrar y manipular datos en un formulario](../../data/odbc/displaying-and-manipulating-data-in-a-form.md)  
  
-   [Trabajar con documentos y vistas](../../data/odbc/working-with-documents-and-views.md)  
  
-   [Acceso a ODBC y SQL](../../data/odbc/access-to-odbc-and-sql.md)  
  
-   [Información adicional sobre las clases ODBC de MFC](../../data/odbc/further-reading-about-the-mfc-odbc-classes.md)  
  
 Las clases de base de datos MFC basadas en ODBC están diseñadas para proporcionar acceso a cualquier base de datos para la que esté disponible un controlador ODBC.  Debido a que las clases utilizan ODBC, la aplicación puede tener acceso a los datos en muchos formatos distintos y diferentes configuraciones locales y remotas.  No es necesario escribir código de casos especiales para controlar distintos sistemas de administración de bases de datos \(DBMS\).  Siempre que los usuarios dispongan de un controlador ODBC adecuado para los datos a los que deseen tener acceso, podrán utilizar el programa para manipular los datos en tablas almacenadas en el mismo.  
  
## Vea también  
 [Conectividad abierta de bases de datos \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)