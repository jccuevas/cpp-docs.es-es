---
title: 'TN048: Escribir programas de instalación y administración de ODBC para aplicaciones de base de datos MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- installing ODBC
- ODBC, installing
- setup, ODBC setup programs
- TN048
- ODBC, and MFC
- MFC, database applications
ms.assetid: d456cdd4-0513-4a51-80c0-9132b66115ce
ms.openlocfilehash: d25520c4ffc805701dfe6b51192f8078e2fa300f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365479"
---
# <a name="tn048-writing-odbc-setup-and-administration-programs-for-mfc-database-applications"></a>TN048: Escribir programas de instalación y administración de ODBC para aplicaciones de base de datos MFC

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Las aplicaciones que usan clases de base de datos MFC necesitarán un programa de instalación que instale componentes ODBC. También pueden necesitar un programa de administración ODBC que recuperará información sobre los controladores disponibles, para especificar controladores predeterminados y para configurar orígenes de datos. Esta nota describe el uso de la API del instalador ODBC para escribir estos programas.

## <a name="writing-an-odbc-setup-program"></a><a name="_mfcnotes_writing_an_odbc_setup_program"></a>Escribir un programa de instalación ODBC

Una aplicación de base de datos MFC requiere el Administrador de controladores ODBC (ODBC. DLL) y controladores ODBC para poder llegar a orígenes de datos. Muchos controladores ODBC también requieren archivos DLL de red y comunicación adicionales. La mayoría de los controladores ODBC se envían con un programa de instalación que instalará los componentes ODBC necesarios. Los desarrolladores de aplicaciones que utilizan clases de base de datos MFC pueden:

- Confíe en los programas de instalación específicos del controlador para instalar componentes ODBC. Esto no requerirá más trabajo por parte del desarrollador, solo puede redistribuir el programa de configuración del controlador.

- Alternativamente, puede escribir su propio programa de instalación, que instalará el administrador de controladores y el controlador.

La API del instalador ODBC se puede utilizar para escribir programas de instalación específicos de la aplicación. Las funciones de la API del instalador se implementan mediante el archivo DLL del instalador ODBC: ODBCINST. DLL en Windows de 16 bits y ODBCCP32. DLL en Win32. Una aplicación `SQLInstallODBC` puede llamar en el archivo DLL del instalador, que instalará el administrador de controladores ODBC, controladores ODBC y los traductores necesarios. A continuación, registra los controladores y traductores instalados en ODBCINST. INI (o el registro, en NT). `SQLInstallODBC`requiere la ruta de acceso completa al ODBC. INF, que contiene la lista de controladores que se van a instalar y describe los archivos que componen cada controlador. También contiene información similar sobre el administrador de controladores y traductores. Odbc. Los archivos INF suelen ser proporcionados por los desarrolladores de controladores.

Un programa también puede instalar componentes ODBC individuales. Para instalar el Administrador de `SQLInstallDriverManager` controladores, un programa primero llama en el archivo DLL del instalador para obtener el directorio de destino para el Administrador de controladores. Este suele ser el directorio en el que residen los archivos DLL de Windows. A continuación, el programa utiliza la información de la sección [Administrador de controladores ODBC] de ODBC. INF para copiar el Administrador de controladores y los archivos relacionados del disco de instalación a este directorio. Para instalar un controlador individual, `SQLInstallDriver` un programa llama primero en el archivo DLL del instalador para agregar la especificación del controlador al ODBCINST. INI (o el registro, en NT). `SQLInstallDriver`devuelve el directorio de destino del controlador, normalmente el directorio en el que residen los archivos DLL de Windows. A continuación, el programa utiliza la información de la sección del controlador de ODBC. INF para copiar el archivo DLL del controlador y los archivos relacionados del disco de instalación a este directorio.

Para obtener más información sobre ODBC. INF, ODBCINST. INI y mediante la API del instalador, consulte Referencia del programador del SDK de *ODBC,* capítulo 19, Instalación del software ODBC.

## <a name="writing-an-odbc-administrator"></a><a name="_mfcnotes_writing_an_odbc_administrator"></a>Escribir un administrador ODBC

Una aplicación de base de datos MFC puede configurar y configurar orígenes de datos ODBC de dos maneras, como se indica a continuación:

- Utilice el Administrador ODBC (disponible como programa o como elemento del Panel de control).

- Cree su propio programa para configurar orígenes de datos.

Un programa que configura orígenes de datos realiza llamadas de función al archivo DLL del instalador. El archivo DLL del instalador llama a un archivo DLL de instalación para configurar un origen de datos. Hay un archivo DLL de instalación para cada controlador; puede ser el propio archivo DLL del controlador, o un archivo DLL independiente. El archivo DLL de instalación solicita al usuario información que el controlador necesita para conectarse al origen de datos y al traductor predeterminado, si se admite. A continuación, llama a la DLL del instalador y a las API de Windows para registrar esta información en ODBC. INI (o registro).

Para mostrar un cuadro de diálogo con el que un usuario `SQLManageDataSources` puede agregar, modificar y eliminar orígenes de datos, un programa llama a la DLL del instalador. Esta función se invoca cuando se llama al archivo DLL del instalador desde el Panel de control. Para agregar, modificar o eliminar `SQLManageDataSources` un `ConfigDSN` origen de datos, llama al archivo DLL de instalación del controlador asociado a ese origen de datos. Para agregar, modificar o eliminar directamente `SQLConfigDataSource` orígenes de datos, un programa llama a la DLL del instalador. El programa pasa el nombre del origen de datos y una opción que especifica la acción a realizar. `SQLConfigDataSource`llama `ConfigDSN` al archivo DLL de instalación y `SQLConfigDataSource`le pasa los argumentos de .

Para obtener más información, vea Referencia del programador del SDK de *ODBC,* Capítulo 23, Referencia de la función DLL de instalación y Capítulo 24, Referencia de la función DLL del instalador.

## <a name="see-also"></a>Consulte también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
