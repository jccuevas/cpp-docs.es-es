---
title: Registro | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1ab5bd34098ee1126e015e2a8368ef5b3c48fdbd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381175"
---
# <a name="registration"></a>Registro
Cuando un usuario desea insertar un elemento OLE en una aplicación, OLE presenta una lista de tipos de objeto que puede elegir. OLE obtiene esta lista de la base de datos de registro de sistema, que contiene la información proporcionada por las aplicaciones de servidor. Cuando un servidor se registra, las entradas que se coloca en la base de datos de registro de sistema (el registro) describen cada tipo de objeto que proporciona, extensiones y la ruta de acceso a sí misma, entre otros datos de archivos.  
  
 El marco de trabajo y las bibliotecas de vínculos dinámicos (DLL) del sistema OLE utilizan este registro para determinar qué tipos de elementos OLE están disponibles en el sistema. El sistema OLE dll también utilizan este registro para determinar cómo iniciar una aplicación de servidor cuando se activa un objeto vinculado o incrustado.  
  
 Este artículo describe lo que cada aplicación de servidor se debe hacer cuando se instala y cada vez que se ejecuta.  
  
 Para obtener información detallada acerca de la base de datos de registro del sistema y el formato de los archivos .reg que se utilizan para actualizarla, vea la *referencia del programador de OLE*.  
  
##  <a name="_core_server_installation"></a> Instalación del servidor  
 Cuando instala por primera vez la aplicación de servidor, deben registrar todos los tipos de elementos OLE que admite. También puede tener el servidor de actualizar la base de datos de registro del sistema cada vez se ejecuta como una aplicación independiente. Esto evita que la base de datos de registro actualizados si se mueve el archivo ejecutable del servidor.  
  
> [!NOTE]
>  Las aplicaciones MFC generadas automáticamente por el Asistente para aplicaciones se registran cuando se ejecutan como aplicaciones independientes.  
  
 Si desea registrar la aplicación durante la instalación, utilice el programa RegEdit.exe. Si incluye un programa de instalación con la aplicación, tener el programa de instalación que se ejecute "RegEdit /S *appname*. reg". (La marca /S indica modo silencioso, es decir, no muestra en el cuadro de diálogo informar sobre la finalización correcta del comando). De lo contrario, pida al usuario que ejecute RegEdit manualmente.  
  
> [!NOTE]
>  El archivo .reg creado por el Asistente para aplicaciones no incluye la ruta de acceso completa para el ejecutable. El programa de instalación debe modificar el archivo .reg para incluir la ruta de acceso completa al archivo ejecutable o modificar la variable de entorno PATH para incluir el directorio de instalación.  
  
 RegEdit combina el contenido del archivo de texto .reg en la base de datos de registro. Para comprobar la base de datos o para repararlo, use el editor del registro. Tenga cuidado para evitar eliminar entradas imprescindibles de OLE.  
  
##  <a name="_core_server_initialization"></a> Inicialización del servidor  
 Cuando se crea una aplicación de servidor con el Asistente para aplicaciones, el asistente completa automáticamente todas las tareas de inicialización para usted. Esta sección describe lo que debe hacer si escribe una aplicación de servidor manualmente.  
  
 Cuando una aplicación de servidor se inicia una aplicación de contenedor, la DLL del sistema OLE agregar la opción "/ incrustación" a la línea de comandos del servidor. Comportamiento de la aplicación de servidor varía en función de si se ha iniciado un contenedor, por lo que lo primero que debe hacer una aplicación cuando inicia la ejecución es buscar el "/ incrustación" o "-Embedding" opción de línea de comandos. Si existe este modificador, cargar un conjunto diferente de recursos que le mostrarán el servidor como cualquier activo en contexto o completamente abierto. Para obtener más información, consulte [menús y recursos: adiciones de servidor](../mfc/menus-and-resources-server-additions.md).  
  
 La aplicación de servidor también debe llamar a su `CWinApp::RunEmbedded` función para analizar la línea de comandos. Si devuelve un valor distinto de cero, la aplicación no debe mostrar su ventana porque se ha ejecutado desde una aplicación de contenedor, no como una aplicación independiente. Esta función actualiza la entrada del servidor en la base de datos de registro de sistema y llama el `RegisterAll` función de miembro para usted, realizando el registro de la instancia.  
  
 Cuando se inicia la aplicación de servidor, debe asegurarse de que puede realizar el registro de la instancia. Registro de la instancia informa a la DLL del sistema OLE que el servidor esté activo y preparado para recibir solicitudes de los contenedores. No se agrega una entrada a la base de datos de registro. Realizar el registro de la instancia del servidor mediante una llamada a la `ConnectTemplate` función de miembro definida por `COleTemplateServer`. Esto conectará el `CDocTemplate` el objeto a la `COleTemplateServer` objeto.  
  
 El `ConnectTemplate` función toma tres parámetros: el servidor **CLSID**, un puntero a la `CDocTemplate` objeto y una marca que indica si el servidor admite varias instancias. Un miniservidor debe ser capaz de admitir varias instancias, es decir, debe ser posible que varias instancias del servidor para ejecutarse de manera simultánea, uno para cada contenedor. Por lo tanto, pasar **TRUE** para este indicador cuando inicie un miniservidor.  
  
 Si está escribiendo un miniservidor, por definición, que siempre se va a iniciar un contenedor. Todavía debe analizar la línea de comandos para comprobar si la opción "/ incrustación". La ausencia de esta opción en la línea de comandos significa que el usuario intentó iniciar el miniservidor como una aplicación independiente. Si esto ocurre, registrar el servidor con la base de datos de registro del sistema y, a continuación, mostrar un cuadro de mensaje que informa al usuario para iniciar el miniservidor como una aplicación de contenedor.  
  
## <a name="see-also"></a>Vea también  
 [OLE](../mfc/ole-in-mfc.md)   
 [Servidores](../mfc/servers.md)   
 [CWinApp::RunAutomated](../mfc/reference/cwinapp-class.md#runautomated)   
 [CWinApp:: RunEmbedded](../mfc/reference/cwinapp-class.md#runembedded)   
 [COleTemplateServer (clase)](../mfc/reference/coletemplateserver-class.md)
