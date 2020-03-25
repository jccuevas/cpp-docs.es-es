---
title: Administrador de ODBC
ms.date: 11/04/2016
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
ms.openlocfilehash: 9e88492919eac80a4f3db2f94202d49011aa69de
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213202"
---
# <a name="odbc-administrator"></a>Administrador de ODBC

El administrador de ODBC registra y configura los [orígenes de datos](../../data/odbc/data-source-odbc.md) disponibles, ya sea de forma local o a través de una red. Los asistentes utilizan la información proporcionada por el Administrador de ODBC para crear en las aplicaciones código que conecta a los usuarios con los orígenes de datos.

Para configurar un origen de datos ODBC para su utilización con las clases ODBC de MFC o con las clases DAO de MFC, primero se debe registrar y configurar el origen de datos. Para agregar y quitar orígenes de datos se ha de utilizar el Administrador de ODBC. Dependiendo del controlador ODBC, se pueden crear también nuevos orígenes de datos.

El Administrador de ODBC se instala durante el proceso de instalación. Si eligió la instalación **personalizada** y no seleccionó ningún controlador ODBC en el cuadro de diálogo **Opciones de base de datos** , deberá volver a ejecutar el programa de instalación para instalar los archivos necesarios.

Durante el proceso de instalación se seleccionan los controladores ODBC que se desea instalar. Posteriormente, se pueden instalar otros controladores que se incluyen en Visual C++ utilizando el programa de instalación de Visual C++.

Si se desea instalar controladores ODBC no incluidos en Visual C++, debe ejecutar el programa de instalación que acompaña al controlador.

#### <a name="to-install-odbc-drivers-that-ship-with-visual-c"></a>Para instalar los controladores ODBC que se incluyen en Visual C++

1. Ejecute el programa de instalación desde el CD de distribución de Visual C++.

   Aparece el cuadro de diálogo inicial del programa de instalación.

1. Haga clic en **siguiente** en cada cuadro de diálogo hasta llegar al cuadro de diálogo **Opciones de instalación** . Seleccione **personalizada**y, a continuación, haga clic en **siguiente**.

1. Desactive todas las casillas del cuadro de diálogo **instalación de C++ Microsoft Visual** , excepto la casilla Opciones de base de **datos** y, a continuación, haga clic en **detalles** para mostrar el cuadro de diálogo Opciones de **base de datos** .

1. Desactive la casilla **Microsoft Data Access Objects** , active la casilla **controladores ODBC de Microsoft** y, a continuación, haga clic en **detalles**.

   Aparecerá el cuadro de diálogo **controladores ODBC de Microsoft** .

1. Seleccione los controladores que desea instalar y, a continuación, haga clic en **Aceptar** dos veces.

1. Haga clic en **siguiente** en el resto de cuadros de diálogo para iniciar la instalación. El programa de instalación notifica cuándo ha finalizado la instalación.

Una vez instalados los controladores, se puede configurar el origen de datos mediante el Administrador de ODBC. El icono ODBC se encuentra en el Panel de control.

## <a name="see-also"></a>Consulte también

[Conectividad abierta de bases de datos (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Origen de datos (ODBC)](../../data/odbc/data-source-odbc.md)
