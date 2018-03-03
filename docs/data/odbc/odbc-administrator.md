---
title: El Administrador de ODBC | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- installing ODBC
- ODBC data sources [C++], ODBC Administrator
- ODBC drivers [C++], installing
- ODBC [C++], ODBC Administrator
- Administrator in ODBC
- administration ODBC Administrator
- ODBC Administrator [C++]
- drivers [C++], ODBC
ms.assetid: b8652790-3437-4e7d-bc83-6ea6981f008b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4a7d60f11457e509ae67da83aa6bc589af1ce43a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-administrator"></a>Administrador de ODBC
El Administrador de ODBC registra y configura el [orígenes de datos](../../data/odbc/data-source-odbc.md) disponibles localmente o a través de una red. Los asistentes utilizan la información proporcionada por el Administrador de ODBC para crear en las aplicaciones código que conecta a los usuarios con los orígenes de datos.  
  
 Para configurar un origen de datos ODBC para su utilización con las clases ODBC de MFC o con las clases DAO de MFC, primero se debe registrar y configurar el origen de datos. Para agregar y quitar orígenes de datos se ha de utilizar el Administrador de ODBC. Dependiendo del controlador ODBC, se pueden crear también nuevos orígenes de datos.  
  
 El Administrador de ODBC se instala durante el proceso de instalación. Si ha elegido **personalizado** instalación y no se ha seleccionado ningún controlador ODBC en el **opciones de base de datos** cuadro de diálogo, debe ejecutar el programa de instalación para instalar los archivos necesarios.  
  
 Durante el proceso de instalación se seleccionan los controladores ODBC que se desea instalar. Posteriormente, se pueden instalar otros controladores que se incluyen en Visual C++ utilizando el programa de instalación de Visual C++.  
  
 Si se desea instalar controladores ODBC no incluidos en Visual C++, debe ejecutar el programa de instalación que acompaña al controlador.  
  
#### <a name="to-install-odbc-drivers-that-ship-with-visual-c"></a>Para instalar los controladores ODBC que se incluyen en Visual C++  
  
1.  Ejecute el programa de instalación desde el CD de distribución de Visual C++.  
  
     Aparece el cuadro de diálogo inicial del programa de instalación.  
  
2.  Haga clic en **siguiente** en cada cuadro de diálogo hasta llegar a la **opciones de instalación** cuadro de diálogo. Seleccione **personalizado**y, a continuación, haga clic en `Next`.  
  
3.  Desactive todas las casillas de verificación en la **el programa de instalación de Microsoft Visual C++** cuadro de diálogo excepto los **opciones de base de datos** casilla de verificación y, a continuación, haga clic en **detalles** para mostrar la **Opciones de base de datos** cuadro de diálogo.  
  
4.  Desactive el **Microsoft Data Access Objects** casilla de verificación, seleccione la **controladores ODBC de Microsoft** casilla de verificación y, a continuación, haga clic en **detalles**.  
  
     El **controladores ODBC de Microsoft** aparece el cuadro de diálogo.  
  
5.  Seleccione los controladores que desea instalar y, a continuación, haga clic en **Aceptar** dos veces.  
  
6.  Haga clic en **siguiente** en los cuadros de diálogo restantes para comenzar la instalación. El programa de instalación notifica cuándo ha finalizado la instalación.  
  
 Una vez instalados los controladores, se puede configurar el origen de datos mediante el Administrador de ODBC. El icono ODBC se encuentra en el Panel de control.  
  
## <a name="see-also"></a>Vea también  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [Origen de datos (ODBC)](../../data/odbc/data-source-odbc.md)