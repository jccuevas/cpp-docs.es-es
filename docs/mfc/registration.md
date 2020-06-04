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
ms.openlocfilehash: 82411e53620e92eff3484f7d3f7955030fd439ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372844"
---
# <a name="registration"></a>Registro

Cuando un usuario desea insertar un elemento OLE en una aplicación, OLE presenta una lista de tipos de objeto para elegir. OLE obtiene esta lista de la base de datos de registro del sistema, que contiene información proporcionada por todas las aplicaciones de servidor. Cuando un servidor se registra, las entradas que coloca en la base de datos de registro del sistema (el Registro) describen cada tipo de objeto que proporciona, extensiones de archivo y la ruta de acceso a sí mismo, entre otra información.

El marco de trabajo y las bibliotecas de vínculos dinámicos (DLL) del sistema OLE usan este registro para determinar qué tipos de elementos OLE están disponibles en el sistema. Los archivos DLL del sistema OLE también usan este registro para determinar cómo iniciar una aplicación de servidor cuando se activa un objeto vinculado o incrustado.

En este artículo se describe lo que cada aplicación de servidor debe hacer cuando se instala y cada vez que se ejecuta.

Para obtener información detallada sobre la base de datos de registro del sistema y el formato de los archivos .reg utilizados para actualizarla, consulte la *referencia del programador OLE*.

## <a name="server-installation"></a><a name="_core_server_installation"></a>Instalación del servidor

La primera vez que instale la aplicación de servidor, debe registrar todos los tipos de elementos OLE que admite. También puede hacer que el servidor actualice la base de datos de registro del sistema cada vez que se ejecute como una aplicación independiente. Esto mantiene la base de datos de registro actualizada si se mueve el archivo ejecutable del servidor.

> [!NOTE]
> Las aplicaciones MFC generadas por el Asistente para aplicaciones se registran automáticamente cuando se ejecutan como aplicaciones independientes.

Si desea registrar la aplicación durante la instalación, utilice el programa RegEdit.exe. Si incluye un programa de instalación con la aplicación, haga que el programa de instalación ejecute "RegEdit /S *appname*.reg". (El indicador /S indica la operación silenciosa, es decir, no muestra el cuadro de diálogo que informa de la finalización correcta del comando.) De lo contrario, indique al usuario que ejecute RegEdit manualmente.

> [!NOTE]
> El archivo .reg creado por el asistente de aplicación no incluye la ruta de acceso completa para el ejecutable. El programa de instalación debe modificar el archivo .reg para incluir la ruta de acceso completa al ejecutable o modificar la variable de entorno PATH para incluir el directorio de instalación.

RegEdit combina el contenido del archivo de texto .reg en la base de datos de registro. Para comprobar la base de datos o repararla, utilice el editor del Registro. Tenga cuidado de evitar eliminar entradas OLE esenciales.

## <a name="server-initialization"></a><a name="_core_server_initialization"></a>Inicialización del servidor

Al crear una aplicación de servidor con el asistente de aplicación, el asistente completa automáticamente todas las tareas de inicialización. En esta sección se describe lo que debe hacer si escribe una aplicación de servidor manualmente.

Cuando una aplicación de servidor se inicia mediante una aplicación contenedora, los archivos DLL del sistema OLE agregan la opción "/Embedding" a la línea de comandos del servidor. El comportamiento de una aplicación de servidor difiere en función de si fue iniciada por un contenedor, por lo que lo primero que una aplicación debe hacer cuando comienza la ejecución es comprobar la opción "/Embedding" o "-Embedding" en la línea de comandos. Si este modificador existe, cargue un conjunto diferente de recursos que muestren que el servidor está activo en el lugar o completamente abierto. Para obtener más información, consulte [Menús y recursos: adiciones](../mfc/menus-and-resources-server-additions.md)de servidor .

La aplicación de servidor `CWinApp::RunEmbedded` también debe llamar a su función para analizar la línea de comandos. Si devuelve un valor distinto de cero, la aplicación no debe mostrar su ventana porque se ha ejecutado desde una aplicación contenedora, no como una aplicación independiente. Esta función actualiza la entrada del servidor en `RegisterAll` la base de datos de registro del sistema y llama a la función miembro por usted, realizando el registro de instancia.

Cuando se inicia la aplicación de servidor, debe asegurarse de que puede realizar el registro de instancias. El registro de instancias informa a los archivos DLL del sistema OLE de que el servidor está activo y listo para recibir solicitudes de contenedores. No agrega una entrada a la base de datos de registro. Realice el registro de instancia `ConnectTemplate` del servidor `COleTemplateServer`llamando a la función miembro definida por . Esto conecta `CDocTemplate` el `COleTemplateServer` objeto con el objeto.

La `ConnectTemplate` función toma tres parámetros: *CLSID*del `CDocTemplate` servidor, un puntero al objeto y un indicador que indica si el servidor admite varias instancias. Un miniservidor debe ser capaz de admitir varias instancias, es decir, debe ser posible que varias instancias del servidor se ejecuten simultáneamente, una para cada contenedor. Por lo tanto, pase **TRUE** para este indicador al iniciar un miniservidor.

Si está escribiendo un miniservidor, por definición siempre será lanzado por un contenedor. Todavía debe analizar la línea de comandos para comprobar la opción "/Incrustar". La ausencia de esta opción en la línea de comandos significa que el usuario ha intentado iniciar el miniservidor como una aplicación independiente. Si esto ocurre, registre el servidor con la base de datos de registro del sistema y, a continuación, muestre un cuadro de mensaje que informe al usuario para iniciar el miniservidor desde una aplicación contenedora.

## <a name="see-also"></a>Consulte también

[OLE](../mfc/ole-in-mfc.md)<br/>
[Servidores](../mfc/servers.md)<br/>
[CWinApp::RunAutomated](../mfc/reference/cwinapp-class.md#runautomated)<br/>
[CWinApp::RunEmbedded](../mfc/reference/cwinapp-class.md#runembedded)<br/>
[COleTemplateServer (clase)](../mfc/reference/coletemplateserver-class.md)
