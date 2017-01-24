---
title: "Conexiones ODBC | Microsoft Docs"
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
  - "conexiones ODBC, configurar"
  - "ODBC, conectividad"
ms.assetid: c9df2fa6-d9e2-4335-b885-724662968691
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Conexiones ODBC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las conexiones ODBC se configuran en el Panel de control del sistema.  Las conexiones ODBC pueden establecerse con cualquier origen de datos para el que haya instalado un controlador ODBC.  Visual C\+\+ 6.0 y las versiones posteriores incluyen controladores para archivos de texto, Access, FoxPro, Paradox, dBASE, Excel, SQL Server y Oracle.  Cuando cree una conexión ODBC, ésta recibirá automáticamente un nombre de origen de datos \(DSN\).  El DSN se utilizará posteriormente para identificar conexiones en controles de datos, como el control de datos ADO y el control RemoteData de RDO.  
  
 **Conexiones OLE DB** No es necesario realizar trabajo adicional para configurar una conexión OLE DB.  Por ejemplo, si se crea un origen de datos ODBC, el proveedor OLE DB para ODBC lo detectará automáticamente.  
  
### Para configurar un origen de datos ODBC  
  
1.  Haga clic en **Inicio**, elija **Configuración** y, a continuación, haga clic en **Panel de control**.  
  
2.  En el Panel de control, seleccione el controlador ODBC de 32 bits \(Windows 95 o Windows 98\) o el controlador ODBC \(Windows NT o Windows 2000\).  
  
3.  Haga clic en la ficha **DSN de usuario** o **DSN de sistema**.  El **DSN de usuario** permite crear nombres de origen de datos específicos del usuario y el **DSN de sistema** permite crear orígenes de datos disponibles para todos los usuarios.  
  
4.  Haga clic en **Agregar** para mostrar una lista de controladores ODBC instalados en el sistema.  
  
5.  Seleccione el controlador que corresponda al tipo de método de acceso secuencial indizado \(ISAM\) o de base de datos con el que desee establecer una conexión y, a continuación, haga clic en **Finalizar**.  
  
6.  Siga las instrucciones especificas para el controlador.  Después de cerrar, el DSN estará disponible para su uso.  
  
 Al generar un DSN para algunos tipos de controlador ODBC, debe conocer la ubicación del archivo.  Por ejemplo, al crear un DSN de Access, debe conocer la ubicación del archivo .mdb.  Además, debe utilizar un nombre de usuario y una contraseña válidos.  Por ejemplo, el nombre de usuario del sistema para la mayoría de los sistemas Access es *admin*.  
  
 Al crear un DSN [Oracle](../../data/ado-rdo/oracle-connections.md) tiene que conocer la cadena de conexión de SQL\*Net.  
  
## Vea también  
 [Crear conexiones de bases de datos](../../data/ado-rdo/creating-database-connections.md)