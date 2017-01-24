---
title: "Crear programas que usan la automatizaci&#243;n remota | Microsoft Docs"
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
  - "automatización remota, crear programas"
ms.assetid: 8eb31320-1037-4029-b1f3-fdc9406dbaf1
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Crear programas que usan la automatizaci&#243;n remota
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cualquier objeto de automatización, y cualquier controlador de automatización, puede utilizar la automatización remota sin ningún cambio en el código fuente, sin necesidad de compilar, y sin necesidad de volver a vincular.  Una vez que se tiene una configuración que funciona localmente \(es decir, en el mismo equipo\), debe recorrer sólo de algunos pasos ejecutarlo remotamente.  
  
#### Para ejecutar el objeto de automatización remota  
  
1.  Registre la aplicación en el equipo cliente o equipos.  
  
2.  Configurar el acceso de cliente al servidor remoto de uso.  
  
3.  Instale y registre la aplicación en el equipo servidor o equipos.  
  
4.  Configurar el servidor permitir la activación remota.  
  
5.  Instale el administrador de automatización en el equipo servidor.  
  
6.  Ejecute el administrador de automatización en servidores.  
  
7.  Ejecute la aplicación en clientes.  
  
 El paso 1 es más fácilmente realizado cargar y ejecutar la aplicación de servidor en el equipo cliente, como la mayoría de los servidores son el registro automático.  Si ya ha probado la configuración local de requisito previo, esta fase ya se ha completado.  Si la aplicación de servidor no es el registro automático, quizás desee poder hacerlo.  De lo contrario, deberá proporcionar un archivo de registro que el usuario local puede ejecutar para realizar este paso.  Si no hace ninguna de estas operaciones, usted o un administrador necesitará editar el registro manualmente, un procedimiento que no se recomienda para todos sólo la mayoría de los usuarios avanzados.  
  
 El paso 2 implica el uso del administrador de Conexión \(RAC\) de automatización remota.  Ejecute el administrador de RAC y asegúrese de que la pestaña de la conexión al servidor es más suprema.  Luego, busque la entrada para el objeto de servidor en el panel de **OLE Classes** y la haga clic en.  Después mueva a **Dirección de red** el cuadro combinado y especifique el nombre del equipo en el que el archivo ejecutable remoto se ejecutará.  Por ejemplo, puede escribir el \\\\MyServer aquí.  A continuación el protocolo de red adecuado de la lista proporcionada.  Puede ser necesario comprobar con el administrador de red para determinar se recomienda qué protocolo.  En muchos casos, este será TCP\/IP.  Finalmente, puede que desee elegir un nivel de autenticación.  En la mayoría de los casos, esto se aplazada como \(None\) o predeterminado.  Ahora haga clic con el botón secundario en el servidor en el panel de **OLE Classes** .  Esto generará un menú contextual del que puede seleccionar el valor local o la operación remota.  Remote seleccione.  
  
 El paso 3 implica correctamente la instalación y el registro de aplicación de servidor en el equipo servidor o equipos seleccionados.  Una vez más si la aplicación es el registro automático, ejecutarlo también lo registrará una vez.  
  
 El paso 4 implica configurar el servidor permitir la ejecución remota.  Ejecute el administrador de RAC en el equipo servidor, y asegúrese de que la ficha de **Acceso de cliente** tiene el foco.  Elija el modelo de activación que desee \(normalmente **Allow Remote Creates by Key**.  Si elige esta opción, también debe hacer clic en la casilla de **Allow Remote Activation** para establecer el valor de la entrada de Registro a “y "\).  Si está ejecutando Windows NT o Windows 2000 y se eligen el remoto de Permitir crea la opción \(ACL\), también debe editar ACL insertando el botón de **Edit ACL** .  
  
 Para permitir que la automatización remota funcione, se debe asegurar que el administrador de automatización está instalado y en ejecución en el equipo servidor o equipos.  Si no está instalada, copie AUTMGR32.EXE el directorio system de Windows.  Para obtener información sobre cómo hacerlo, vea [Instalación de automatización remota](../mfc/remote-automation-installation.md).  Para iniciar la automatización remota, ejecute el administrador de automatización.  Mostrará una pequeña ventana de estado en la que varios mensajes se muestran.  Una vez que se haya iniciado, se minimizará.  Si desea continuar consultando la información de estado, puede hacer clic en la ficha de **Automation Manager** en la barra de tareas para restaurar la ventana.  
  
 El paso final es ejecutar la aplicación cliente en el equipo cliente.  Si ha seguido los pasos anteriores, debe conectar con el objeto de servidor y ejecutar exactamente como lo hizo localmente, no obstante un poco más lento.  
  
 Observe que el administrador de RAC también permite alternar entre la automatización remota como COM distribuido \(DCOM, en estas plataformas que DCOM admiten\) con un solo clic de un botón de opción.  Si elige DCOM, puede establecer otras opciones de configuración.  Vea la documentación de DCOM para obtener detalles adicionales.  
  
## Vea también  
 [Automatización remota](../mfc/remote-automation.md)   
 [Ejecutar la automatización remota mediante AUTOCLIK y AUTODRIV](../mfc/running-remote-automation-using-autoclik-and-autodriv.md)