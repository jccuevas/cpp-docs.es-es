---
title: Registro
ms.date: 11/04/2016
helpviewer_keywords:
- servers [MFC], initializing
- initializing servers [MFC]
- OLE, registration
- installing servers [MFC]
- registry [MFC], OLE item database
- registration databases [MFC]
- servers [MFC], installing
- OLE server applications [MFC], registering servers
ms.assetid: 991d5684-72c1-4f9e-a09a-9184ed12bbb9
ms.openlocfilehash: 0bc606acfba26d27d0ab36045e4772593e760e98
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272179"
---
# <a name="registration"></a>Registro

Cuando un usuario desea insertar un elemento OLE en una aplicación, OLE presenta una lista de tipos de objeto que puede elegir. OLE obtiene esta lista de la base de datos de registro del sistema, que contiene la información proporcionada por todas las aplicaciones de servidor. Cuando un servidor se registra, las entradas que coloca en la base de datos de registro del sistema (el registro) describen cada tipo de objeto que proporciona, extensiones y la ruta de acceso a sí misma, entre otros datos de archivo.

El marco de trabajo y las bibliotecas de vínculos dinámicos de sistema (DLL) de OLE utilizan este registro para determinar qué tipos de elementos OLE están disponibles en el sistema. El sistema OLE dll también utiliza este registro para determinar cómo iniciar una aplicación de servidor cuando se activa un objeto vinculado o incrustado.

Este artículo describe lo que debe hacer cuando se instala cada aplicación de servidor y cada vez que se ejecuta.

Para obtener información detallada acerca de la base de datos de registro del sistema y el formato de los archivos .reg que se utilizan para actualizarla, consulte el *referencia del programador OLE*.

##  <a name="_core_server_installation"></a> Instalación del servidor

Cuando instala por primera vez la aplicación de servidor, deben registrar todos los tipos de elementos OLE que admite. También puede tener el servidor de actualización de la base de datos de registro del sistema cada vez se ejecuta como una aplicación independiente. Esto mantiene actualizada la base de datos de registro si se mueve el archivo ejecutable del servidor.

> [!NOTE]
>  Las aplicaciones MFC generadas automáticamente el Asistente para aplicaciones se registran cuando se ejecutan como aplicaciones independientes.

Si desea registrar la aplicación durante la instalación, use el programa RegEdit.exe. Si incluye un programa de instalación con la aplicación, se ejecuta el programa de instalación "RegEdit /S *appname*. reg". (La marca /S indica una operación silenciosa, es decir, no muestra el cuadro de diálogo informar sobre la finalización correcta del comando). De lo contrario, pida al usuario ejecutar RegEdit manualmente.

> [!NOTE]
>  El archivo .reg creado por el Asistente para aplicaciones no incluye la ruta de acceso completa del ejecutable. El programa de instalación debe modificar el archivo .reg para incluir la ruta de acceso completa al archivo ejecutable o modificar la variable de entorno PATH para incluir el directorio de instalación.

RegEdit combina el contenido del archivo de texto .reg en la base de datos de registro. Para comprobar la base de datos o para repararlo, utilice el editor del registro. Tenga cuidado para evitar la eliminación de entradas imprescindibles de OLE.

##  <a name="_core_server_initialization"></a> Inicialización del servidor

Cuando se crea una aplicación de servidor con el Asistente para aplicaciones, el asistente completa automáticamente todas las tareas de inicialización por usted. En esta sección se describe lo que debe hacer si escribe una aplicación de servidor manualmente.

Cuando una aplicación de servidor se inicia una aplicación contenedora, la DLL del sistema OLE agregue la opción "/ incrustación" a la línea de comandos del servidor. Comportamiento de la aplicación de servidor depende de si se ha iniciado un contenedor, por lo que lo primero que debe hacer una aplicación cuando comienza la ejecución es la comprobación de la "/ incrustación" o "-Embedding" opción en la línea de comandos. Si no existe este modificador, cargar un conjunto diferente de los recursos que muestran el servidor como cualquier activo en contexto o completamente abierto. Para obtener más información, consulte [menús y recursos: Adiciones de servidor](../mfc/menus-and-resources-server-additions.md).

La aplicación de servidor también debe llamar a su `CWinApp::RunEmbedded` función para analizar la línea de comandos. Si devuelve un valor distinto de cero, la aplicación no debe mostrar su ventana porque se ha ejecutado desde una aplicación de contenedor, no como una aplicación independiente. Esta función actualiza la entrada de servidor en la base de datos de registro del sistema y llama a la `RegisterAll` la función miembro para usted, realizar el registro de la instancia.

Cuando se inicia la aplicación de servidor, debe asegurarse de que puede realizar el registro de la instancia. Registro de la instancia informa a la DLL del sistema OLE que el servidor esté activo y listo para recibir solicitudes de los contenedores. No se agrega una entrada a la base de datos de registro. Realizar el registro de la instancia del servidor mediante una llamada a la `ConnectTemplate` función de miembro definida por `COleTemplateServer`. Esto conectará el `CDocTemplate` de objeto para el `COleTemplateServer` objeto.

El `ConnectTemplate` función toma tres parámetros: el servidor *CLSID*, un puntero a la `CDocTemplate` objeto y una marca que indica si el servidor admite varias instancias. Un miniservidor debe ser capaz de admitir varias instancias, es decir, debe ser posible que varias instancias del servidor para ejecutarse de manera simultánea, uno para cada contenedor. Por lo tanto, pasar **TRUE** de esta marca cuando inicie un miniservidor.

Si está escribiendo un miniservidor, por definición, siempre se iniciará un contenedor. Todavía debe analizar la línea de comandos para comprobar si la opción "/ incrustación". La ausencia de esta opción en la línea de comandos significa que el usuario ha intentado iniciar el miniservidor como una aplicación independiente. Si esto ocurre, registrar el servidor con la base de datos de registro del sistema y, a continuación, mostrar un cuadro de mensaje que informa al usuario para iniciar el miniservidor desde una aplicación contenedora.

## <a name="see-also"></a>Vea también

[OLE](../mfc/ole-in-mfc.md)<br/>
[Servidores](../mfc/servers.md)<br/>
[CWinApp::RunAutomated](../mfc/reference/cwinapp-class.md#runautomated)<br/>
[CWinApp::RunEmbedded](../mfc/reference/cwinapp-class.md#runembedded)<br/>
[COleTemplateServer (clase)](../mfc/reference/coletemplateserver-class.md)
