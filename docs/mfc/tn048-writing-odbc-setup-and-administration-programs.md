---
title: 'TN048: Escribir programas de administración y el programa de instalación ODBC para aplicaciones de base de datos MFC | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.odbc
dev_langs:
- C++
helpviewer_keywords:
- installing ODBC
- ODBC, installing
- setup, ODBC setup programs
- TN048
- ODBC, and MFC
- MFC, database applications
ms.assetid: d456cdd4-0513-4a51-80c0-9132b66115ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a7d89b6c6e05a5baf973abace2c64de3b52754f5
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954562"
---
# <a name="tn048-writing-odbc-setup-and-administration-programs-for-mfc-database-applications"></a>TN048: Escribir programas de instalación y administración de ODBC para aplicaciones de base de datos MFC
> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Las aplicaciones que usan las clases de base de datos MFC necesitará un programa de instalación que instala los componentes de ODBC. También tendrá un programa de administración de ODBC que se recuperará automáticamente información acerca de los controladores disponibles, para especificar controladores de forma predeterminada y configurar orígenes de datos. Esta nota describe el uso de la API del instalador de ODBC para escribir estos programas.  
  
##  <a name="_mfcnotes_writing_an_odbc_setup_program"></a> Escribir un programa de instalación ODBC  
 Una aplicación de base de datos MFC requiere que el Administrador de controladores ODBC (ODBC. DLL) y controladores ODBC para poder llegar a los orígenes de datos. Muchos controladores ODBC también requieren archivos DLL adicionales de red y la comunicación. Mayoría de los controladores ODBC que se distribuye con un programa de instalación que instalará los componentes ODBC necesarios. Los desarrolladores de aplicaciones mediante clases de base de datos MFC pueden:  
  
-   Se basan en los programas de configuración específico del controlador para instalar los componentes ODBC. Será necesario ningún otro trabajo por parte del desarrollador, simplemente puede redistribuir el programa de instalación del controlador.  
  
-   Como alternativa, puede escribir su propio programa de instalación, que se va a instalar el Administrador de controladores y el controlador.  
  
 La API del instalador ODBC puede utilizarse para escribir programas de instalación específicos de la aplicación. Las funciones de la API del instalador se implementan mediante el archivo DLL del instalador ODBC: ODBCINST. DLL de Windows de 16 bits y ODBCCP32. DLL de Win32. Una aplicación puede llamar a `SQLInstallODBC` en el instalador de DLL, que se va a instalar el Administrador de controladores ODBC, controladores ODBC y cualquier necesario traductores. A continuación, registra los controladores instalados y traductores en el ODBCINST. El archivo INI (o el registro de NT). `SQLInstallODBC` requiere la ruta de acceso completa de ODBC. Archivo INF, que contiene la lista de controladores se instalen y se describe los archivos que componen cada controlador. También contiene información similar sobre el Administrador de controladores y traductores. ODBC. Los desarrolladores de controladores normalmente proporciona archivos INF.  
  
 Un programa también puede instalar los componentes individuales de ODBC. Para instalar el Administrador de controladores, un programa llama primero `SQLInstallDriverManager` en el instalador de DLL para obtener el directorio de destino para el Administrador de controladores. Por lo general, suele ser el directorio en el que residen los archivos DLL de Windows. A continuación, el programa utiliza la información en la sección [ODBC Driver Manager] de ODBC. Archivo INF para copiar los archivos relacionados y el Administrador de controladores desde el disco de instalación en este directorio. Para instalar un controlador individual, un programa llama primero `SQLInstallDriver` en el archivo DLL para agregar la especificación de controlador para el ODBCINST del instalador. El archivo INI (o el registro de NT). `SQLInstallDriver` Devuelve el directorio de destino del controlador, normalmente el directorio en el que residen los archivos DLL de Windows. A continuación, el programa utiliza la información en la sección del controlador de ODBC. Archivo INF para copiar la DLL del controlador y los archivos relacionados desde el disco de instalación en este directorio.  
  
 Para obtener más información acerca de ODBC. INF, ODBCINST. INI y mediante el instalador de API, consulte el SDK de ODBC *referencia del programador,* capítulo 19, la instalación del Software de ODBC.  
  
##  <a name="_mfcnotes_writing_an_odbc_administrator"></a> Escribir un administrador ODBC  
 Una aplicación de base de datos MFC puede instalar y configurar orígenes de datos ODBC en una de dos maneras, como se indica a continuación:  
  
-   Use el Administrador de ODBC (disponible como un programa o como un elemento del Panel de Control).  
  
-   Cree su propio programa para configurar orígenes de datos.  
  
 Un programa que configura los orígenes de datos realiza llamadas a función en el archivo DLL del instalador. El instalador DLL llama a un archivo DLL para configurar un origen de datos de configuración. Hay un archivo DLL de configuración para cada controlador; puede ser el propio archivo DLL del controlador o un archivo DLL independiente. El archivo DLL del programa de instalación pide al usuario información que el controlador necesita para conectarse al origen de datos y el traductor de manera predeterminada, si se admite. A continuación, se llama al instalador DLL y las API de Windows para registrar esta información en el SDK de ODBC. El archivo INI (o registro).  
  
 Para mostrar un cuadro de diálogo con el que un usuario puede agregar, modificar y eliminar orígenes de datos, un programa llama a `SQLManageDataSources` en el archivo DLL del instalador. Esta función se invoca cuando el programa de instalación es llamar a la DLL desde el Panel de Control. Para agregar, modificar o eliminar un origen de datos, `SQLManageDataSources` llamadas `ConfigDSN` en el archivo DLL del programa de instalación para el controlador asociado con ese origen de datos. Para agregar, modificar o eliminar datos directamente orígenes, las llamadas de un programa `SQLConfigDataSource` en el archivo DLL del instalador. El programa pasa el nombre del origen de datos y una opción que especifica la acción que se realizará. `SQLConfigDataSource` llamadas `ConfigDSN` en la configuración del archivo DLL y pasa los argumentos de `SQLConfigDataSource`.  
  
 Para obtener más información, vea el SDK de ODBC *referencia del programador,* capítulo 23, referencia de funciones de DLL el programa de instalación y capítulo 24, referencia función DLL del instalador.  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

