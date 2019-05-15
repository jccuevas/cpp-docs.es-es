---
title: 'TN048: Escribir programas de administración y configuración de ODBC para aplicaciones de base de datos MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- installing ODBC
- ODBC, installing
- setup, ODBC setup programs
- TN048
- ODBC, and MFC
- MFC, database applications
ms.assetid: d456cdd4-0513-4a51-80c0-9132b66115ce
ms.openlocfilehash: ec74b75ff34c98a9231582b3db411fda90c5a9ff
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2019
ms.locfileid: "65612134"
---
# <a name="tn048-writing-odbc-setup-and-administration-programs-for-mfc-database-applications"></a>TN048: Escribir programas de administración y configuración de ODBC para aplicaciones de base de datos MFC

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Las aplicaciones que usan las clases de base de datos MFC necesitará un programa de instalación que instala los componentes ODBC. También pueden necesitar un programa de administración de ODBC que se recuperará la información acerca de los controladores disponibles, para especificar controladores predeterminados y para configurar orígenes de datos. Esta nota describe el uso de la API del instalador ODBC para escribir estos programas.

##  <a name="_mfcnotes_writing_an_odbc_setup_program"></a> Escribir un programa de instalación ODBC

Una aplicación de base de datos MFC requiere que el Administrador de controladores ODBC (ODBC. DLL) y controladores ODBC para poder acceder a orígenes de datos. Muchos controladores ODBC también requieren la DLL de red y comunicación adicionales. La mayoría de los controladores ODBC se distribuyen con un programa de instalación que va a instalar los componentes ODBC necesarios. Los desarrolladores de aplicaciones mediante las clases de base de datos MFC pueden:

- Se basan en los programas de configuración específico del controlador para instalar los componentes ODBC. Esto requerirá ningún otro esfuerzo por parte del desarrollador, simplemente puede redistribuir el programa de instalación del controlador.

- Como alternativa, puede escribir su propio programa de instalación, lo que instalará el Administrador de controladores y el controlador.

La API del instalador ODBC puede usarse para escribir programas de instalación específicos de la aplicación. Las funciones en el instalador de API se implementan mediante el archivo DLL de instalador ODBC: ODBCINST. DLL de Windows de 16 bits y ODBCCP32. DLL de Win32. Una aplicación puede llamar a `SQLInstallODBC` en el instalador de DLL, que se instalará el Administrador de controladores ODBC, los controladores ODBC y cualquier necesario traductores. A continuación, registra los controladores instalados y traductores en el ODBCINST. Archivo INI (o el registro de NT). `SQLInstallODBC` requiere la ruta de acceso completa de ODBC. Archivo INF, que contiene la lista de controladores se instalen y se describe los archivos que componen cada controlador. También contiene información similar sobre el Administrador de controladores y traductores. ODBC. Normalmente se suministran archivos INF por desarrolladores de controladores.

Un programa también puede instalar componentes individuales de ODBC. Para instalar el Administrador de controladores, un programa llama primero `SQLInstallDriverManager` en el instalador de DLL para obtener el directorio de destino para el Administrador de controladores. Esto suele ser el directorio en el que residen los archivos DLL de Windows. El programa, a continuación, usa la información en la sección [ODBC Driver Manager] de ODBC. Archivo INF para copiar los archivos relacionados y el Administrador de controladores desde el disco de instalación para este directorio. Para instalar un controlador individual, un programa llama primero `SQLInstallDriver` en el archivo DLL para agregar la especificación de controlador para el ODBCINST del instalador. Archivo INI (o el registro de NT). `SQLInstallDriver` Devuelve el directorio de destino del controlador, normalmente el directorio en el que residen los archivos DLL de Windows. El programa, a continuación, usa la información de la sección del controlador de ODBC. Archivo INF para copiar la DLL del controlador y los archivos relacionados desde el disco de instalación en este directorio.

Para obtener más información acerca de ODBC. INF, ODBCINST. INI y mediante el instalador de API, consulte el SDK de ODBC *referencia del programador,* capítulo 19, instalar Software de ODBC.

##  <a name="_mfcnotes_writing_an_odbc_administrator"></a> Escribir un administrador ODBC

Una aplicación de base de datos MFC puede instalar y configurar orígenes de datos ODBC en una de dos maneras, como se indica a continuación:

- Utilice el Administrador de ODBC (disponible como un programa o como un elemento del Panel de Control).

- Cree su propio programa para configurar orígenes de datos.

Un programa que configura los orígenes de datos realiza llamadas de función a la DLL de instalador. El instalador de DLL llama a un archivo DLL para configurar un origen de datos de configuración. Hay un archivo DLL de configuración para cada controlador; puede ser el propio archivo DLL del controlador o un archivo DLL independiente. El archivo DLL de configuración solicita al usuario para obtener información que el controlador necesita para conectarse al origen de datos y el traductor de forma predeterminada, si se admite. A continuación, se llama al instalador DLL y las API de Windows para registrar esta información en ODBC. Archivo INI (o registro).

Para mostrar un cuadro de diálogo con el que un usuario puede agregar, modificar y eliminar orígenes de datos, un programa llama a `SQLManageDataSources` en el archivo DLL de instalador. Esta función se invoca cuando el instalador de DLL se llama desde el Panel de Control. Para agregar, modificar o eliminar un origen de datos, `SQLManageDataSources` llamadas `ConfigDSN` en el archivo DLL de configuración para el controlador asociado con ese origen de datos. Para agregar, modificar o eliminar datos directamente orígenes, llama un programa `SQLConfigDataSource` en el archivo DLL de instalador. El programa pasa el nombre del origen de datos y una opción que especifica la acción que se realizará. `SQLConfigDataSource` las llamadas `ConfigDSN` en la configuración del archivo DLL y le pasa los argumentos de `SQLConfigDataSource`.

Para obtener más información, consulte el SDK de ODBC *referencia del programador,* capítulo 23, referencia de funciones DLL de instalación y capítulo 24, referencia de funciones DLL de instalador.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
