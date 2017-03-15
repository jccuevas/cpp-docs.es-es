---
title: "Administrador de ODBC | Microsoft Docs"
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
  - "administración, Administrador de ODBC"
  - "Administrador de ODBC"
  - "controladores [C++], ODBC"
  - "instalar ODBC"
  - "ODBC [C++], Administrador de ODBC"
  - "Administrador de ODBC [C++]"
  - "orígenes de datos ODBC [C++], Administrador de ODBC"
  - "controladores ODBC [C++], instalar"
ms.assetid: b8652790-3437-4e7d-bc83-6ea6981f008b
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Administrador de ODBC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El Administrador de ODBC registra y configura los [orígenes de datos](../../data/odbc/data-source-odbc.md) disponibles, ya sea localmente o a través de una red.  Los asistentes utilizan la información proporcionada por el Administrador de ODBC para crear en las aplicaciones código que conecta a los usuarios con los orígenes de datos.  
  
 Para configurar un origen de datos ODBC para su utilización con las clases ODBC de MFC o con las clases DAO de MFC, primero se debe registrar y configurar el origen de datos.  Para agregar y quitar orígenes de datos se ha de utilizar el Administrador de ODBC.  Dependiendo del controlador ODBC, se pueden crear también nuevos orígenes de datos.  
  
 El Administrador de ODBC se instala durante el proceso de instalación.  Si se ha elegido la instalación **Personalizada** y no se ha seleccionado ningún controlador ODBC en el cuadro de diálogo **Opciones de base de datos**, es necesario volver a ejecutar el programa de instalación para instalar los archivos necesarios.  
  
 Durante el proceso de instalación se seleccionan los controladores ODBC que se desea instalar.  Posteriormente, se pueden instalar otros controladores que se incluyen en Visual C\+\+ utilizando el programa de instalación de Visual C\+\+.  
  
 Si se desea instalar controladores ODBC no incluidos en Visual C\+\+, debe ejecutar el programa de instalación que acompaña al controlador.  
  
#### Para instalar los controladores ODBC que se incluyen en Visual C\+\+  
  
1.  Ejecute el programa de instalación desde el CD de distribución de Visual C\+\+.  
  
     Aparece el cuadro de diálogo inicial del programa de instalación.  
  
2.  Haga clic en **Siguiente** en cada cuadro de diálogo que vaya apareciendo hasta llegar al cuadro de diálogo **Opciones de instalación**.  Seleccione **Personalizada** y, a continuación, haga clic en `Next`.  
  
3.  Desactive todas las casillas del cuadro de diálogo **Instalación de Microsoft Visual C\+\+** excepto la casilla **Opciones de base de datos** y, a continuación, haga clic en **Detalles** para mostrar el cuadro de diálogo **Opciones de base de datos**.  
  
4.  Desactive la casilla **Objetos de acceso a datos de Microsoft**, active la casilla **Controladores ODBC de Microsoft** y, a continuación, haga clic en **Detalles**.  
  
     Aparece el cuadro de diálogo **Controladores ODBC de Microsoft**.  
  
5.  Seleccione los controladores que desee instalar y, después, haga doble clic en **Aceptar**.  
  
6.  Haga clic en **Siguiente** en los restantes cuadros de diálogo para empezar la instalación.  El programa de instalación notifica cuándo ha finalizado la instalación.  
  
 Una vez instalados los controladores, se puede configurar el origen de datos mediante el Administrador de ODBC.  El icono ODBC se encuentra en el Panel de control.  
  
## Vea también  
 [Conectividad abierta de bases de datos \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)   
 [Origen de datos \(ODBC\)](../../data/odbc/data-source-odbc.md)