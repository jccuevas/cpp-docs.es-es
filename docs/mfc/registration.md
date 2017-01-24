---
title: "Registro | Microsoft Docs"
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
  - "inicializar servidores"
  - "instalar servidores"
  - "aplicaciones de servidor OLE, registrar servidores"
  - "OLE, registro"
  - "registro de bases de datos"
  - "Registro, elemento de base de datos OLE"
  - "servidores, inicializar"
  - "servidores, instalar"
ms.assetid: 991d5684-72c1-4f9e-a09a-9184ed12bbb9
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Registro
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando un usuario desea insertar un elemento OLE en una aplicación, OLE muestra una lista de tipos de objeto para elegir.  OLE obtiene esta lista de base de datos de registro del sistema, que contiene la información proporcionada por todas las aplicaciones de servidor.  Cuando un servidor está registrado, las entradas que coloca en la base de datos de registro del sistema \(el registro\) describe cada tipo de objeto que proporciona, las extensiones de archivo, y la ruta de acceso a sí mismo, entre otra información.  
  
 El marco y bibliotecas de vínculos dinámicos VIEJAS \(DLL\) de sistema utilizan este registro para determinar qué tipos de elementos de OLE están disponibles en el sistema.  Los archivos DLL de OLE system también utilizan este registro para determinar cómo iniciar una aplicación de servidor cuando se activa un objeto vinculado o incrustado.  
  
 En este artículo se describe lo que necesita cada aplicación de servidor hacer cuando se instala y se ejecuta cada vez.  
  
 Para obtener información detallada sobre la base de datos de registro del sistema y el formato de los archivos .reg utilizados para actualizarlo, vea *referencia\) del Programador*.  
  
##  <a name="_core_server_installation"></a> Instalación de Servidor  
 Al instalar primero la aplicación de servidor, debe registrar todos los tipos de elementos de OLE que admite.  También puede tener el servidor actualiza la base de datos de registro del sistema cada vez que se ejecuta como una aplicación independiente.  Esto mantiene la base de datos de registro actualizada si se mueve el archivo ejecutable del servidor.  
  
> [!NOTE]
>  Las aplicaciones MFC generadas por el asistente para aplicaciones automáticamente se registran cuando se ejecutan como aplicaciones independientes.  
  
 Si desea registrar la aplicación durante la instalación, use el programa de RegEdit.exe. \(En Windows 95, Windows 98, y Windows Me, RegEdit está en el directorio de Windows.  En Windows NT y Windows 2000, RegEdit está en el directorio de Windows System32.\) Si incluye un programa de instalación con la aplicación, tiene el “RegEdit ejecuta el programa de instalación \/S *appname.reg*”. \(Relativo a La \/S indica la operación silenciosa, es decir, no muestra el cuadro de diálogo que señala la finalización correcta del comando.\) Si no, indique al usuario para ejecutar RegEdit manualmente.  
  
> [!NOTE]
>  El archivo .reg creado por el asistente para aplicaciones no incluye la ruta de acceso completa para el ejecutable.  El programa de instalación debe modificar el archivo .reg para incluir la ruta de acceso completa al archivo ejecutable o modificar la variable de entorno PATH para incluir el directorio de instalación.  
  
 RegEdit combina el contenido del archivo de texto .reg en la base de datos de registro.  Para comprobar la base de datos o repararla, utilice el editor del Registro.  Tenga cuidado de no eliminar las entradas básicos de OLE. \(En Windows 95, Windows 98, y Windows Me, el editor del Registro es RegEdit.exe.  En Windows NT y Windows 2000, es RegEdit32.exe.\)  
  
##  <a name="_core_server_initialization"></a> Inicialización del Servidor  
 Cuando crea una aplicación de servidor con el asistente para aplicaciones, el asistente completa todas las tareas de inicialización automáticamente.  Esta sección describe lo que debe hacer si escribe una aplicación de servidor manualmente.  
  
 Cuando una aplicación de servidor es iniciada por una aplicación contenedora, los archivos DLL del sistema OLE agregan la opción “\/Embedding” a la línea de comandos del servidor.  Un comportamiento de servidor difiere en función de si se inició por un contenedor, lo que lo primero aplicación debe hacer cuando comienza la ejecución se comprueba la “\/Embedding” o “\- opción de incrustación” en la línea de comandos.  Si existe este modificador, cargue un conjunto diferente de recursos que muestran el servidor como permanece activo en contexto o inicien totalmente.  Para obtener más información, vea [Menús y recursos: Adiciones de Servidor](../mfc/menus-and-resources-server-additions.md).  
  
 La aplicación de servidor debe llamar a la función de `CWinApp::RunEmbedded` para analizar la línea de comandos.  Si devuelve un valor distinto de cero, la aplicación no debe mostrar la ventana porque se ha ejecutado de aplicación contenedora, no como una aplicación independiente.  Esta función actualiza la entrada de servidor en la base de datos de registro del sistema y llama a la función miembro de `RegisterAll` para usted, realizando el registro de la instancia.  
  
 Cuando la aplicación de servidor está iniciando, debe asegurarse de que puede realizar el registro de la instancia.  El registro de la instancia informa a los archivos DLL del sistema OLE que el servidor está activo y listo para recibir solicitudes de contenedores.  No agrega una entrada a la base de datos de registro.  Realice el registro de la instancia del servidor llamando a la función miembro de `ConnectTemplate` definida por `COleTemplateServer`.  Esto conecta el objeto de `CDocTemplate` al objeto de `COleTemplateServer` .  
  
 La función de `ConnectTemplate` toma tres parámetros: **CLSID**de servidor, un puntero al objeto de `CDocTemplate` , y una marca que indica si el servidor admite varias instancias.  Un miniserver debe poder admitir varias instancias, es decir, debe ser posible que varias instancias de servidor se ejecutan simultáneamente, uno para cada contenedor.  Por consiguiente, paso **VERDADERO** para este marcador al iniciar un miniserver.  
  
 Si está escribiendo un miniserver, por definición se iniciará siempre por un contenedor.  Aún debe analizar la línea de comandos para comprobar la opción “\/Embedding”.  La ausencia de esta opción de la línea de comandos significa que el usuario ha intentado iniciar el miniserver como aplicación independiente.  Si ocurre esto, registre el servidor con la base de datos de registro del sistema y envíe un cuadro de mensaje que informa al usuario para iniciar el miniserver de aplicación contenedora.  
  
## Vea también  
 [OLE](../mfc/ole-in-mfc.md)   
 [Servidores](../mfc/servers.md)   
 [CWinApp::RunAutomated](../Topic/CWinApp::RunAutomated.md)   
 [CWinApp::RunEmbedded](../Topic/CWinApp::RunEmbedded.md)   
 [COleTemplateServer Class](../mfc/reference/coletemplateserver-class.md)