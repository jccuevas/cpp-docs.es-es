---
title: "Crear programas que usan la automatización remota | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Remote Automation, creating programs
ms.assetid: 8eb31320-1037-4029-b1f3-fdc9406dbaf1
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: deb832e0baed30507ef3f9929fb5f12805b7a807
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="creating-programs-that-use-remote-automation"></a>Crear programas que usan la automatización remota
Cualquier objeto de automatización y cualquier controlador de automatización, es capaz de utilizar la automatización remota sin ningún cambio en el código fuente, sin necesidad de volver a compilar y sin necesidad de volver a vincular. Una vez que tenga una instalación que funciona localmente (es decir, en el mismo equipo), tendrá que realizar solo unos pocos pasos para ejecutar de forma remota.  
  
#### <a name="to-execute-the-remote-automation-object"></a>Para ejecutar el objeto de automatización remota  
  
1.  Registre la aplicación en el equipo cliente o máquinas.  
  
2.  Configurar el acceso de cliente para usar el servidor remoto.  
  
3.  Instale y registre la aplicación en el equipo de servidor o equipos.  
  
4.  Configurar el servidor para permitir la activación remota.  
  
5.  Instale al administrador de automatización en los equipos de servidor.  
  
6.  Ejecute el Administrador de automatización en los servidores.  
  
7.  Ejecute la aplicación en los clientes.  
  
 Paso 1 se consigue más fácilmente al cargar y ejecutar la aplicación de servidor en el equipo cliente, ya que la mayoría de los servidores son registran automáticamente. Si ha probado la instalación local con antelación, esta fase ya está completa. Si la aplicación de servidor no se registra automáticamente, puede que desee para que sea así. En caso contrario, debe proporcionar un archivo de registro que el usuario local puede ejecutar para realizar este paso. Si lo hace, ninguna de estas cosas, usted o un administrador necesitará editar el registro manualmente, un procedimiento que no se recomienda para todas los usuarios más avanzados.  
  
 Paso 2 implica el uso del Administrador de conexiones de automatización remota (RAC). Ejecute el Administrador de RAC y asegúrese de que la pestaña de la conexión de servidor es superior. A continuación, busque la entrada para el objeto de servidor en el **clases OLE** panel y haga clic en él. Desplazarse a la **dirección de red** combinado cuadro y escriba el nombre de la máquina del servidor en el que se ejecutará el archivo ejecutable remoto. Por ejemplo, puede escribir \\\MyServer aquí. A continuación, elija el protocolo de red adecuada de la lista proporcionada. Puede que necesite póngase en contacto con el Administrador de red para determinar qué protocolo se recomienda. En muchos casos, se trata de TCP/IP. Por último, puede que desee elegir un nivel de autenticación. En la mayoría de los casos, esto será dejará como (ninguno) o predeterminado. Ahora haga clic en el servidor en el **clases OLE** panel. Esto creará un acceso directo en el que puede seleccionar funcionamiento local o remoto. Seleccione remoto.  
  
 Paso 3 implica instala y registra la aplicación de servidor en el equipo de servidor seleccionado o máquinas correctamente. Una vez más, si la aplicación se registran automáticamente, ejecute por primera vez lo también registrará.  
  
 Paso 4 implica configurar el servidor para permitir la ejecución remota. Ejecutar el Administrador de RAC en el equipo del servidor y asegúrese de que el **acceso de cliente** ficha tiene el foco. Elija el modelo de activación que desee (normalmente **permitir remoto crea clave**. Si elige esta opción, también debe hacer clic en el **permitir activación remota** casilla de verificación para establecer el valor de la entrada del registro en 'Y'). Si está ejecutando Windows NT o Windows 2000 y se elige la opción Permitir creaciones remotas (ACL), también tiene la opción para editar la ACL insertando el **editar ACL** botón.  
  
 Para permitir la automatización remota para que funcione, debe para asegurarse de que el Administrador de automatización está instalado y ejecutándose en el equipo de servidor o equipos. Si no está instalado, copie el archivo AUTMGR32. EXE en el directorio de sistema de Windows. Para obtener información sobre cómo hacerlo, consulte [instalación de automatización remota](../mfc/remote-automation-installation.md). Para iniciar la automatización remota, ejecute el Administrador de automatización. Se mostrará una pequeña ventana de estado en el que se mostrará un número de mensajes. Una vez que se ha iniciado, se minimizará. Si desea continuar ver información de estado, haga clic en el **Administrador de automatización** ficha en la barra de tareas para restaurar la ventana.  
  
 El último paso es ejecutar la aplicación cliente en el equipo cliente. Si ha seguido los pasos anteriores, debe conectar con el objeto de servidor y ejecutar exactamente como lo hizo de forma local, aunque sea un poco más lento.  
  
 Tenga en cuenta que el Administrador de conexiones también permite cambiar entre la automatización remota y COM distribuido (DCOM, en estas plataformas que admiten DCOM) con un solo clic de un botón de radio. Si elige DCOM, puede establecer varias opciones de configuración. Consulte la documentación de DCOM para obtener más detalles.  
  
## <a name="see-also"></a>Vea también  
 [Automatización remota](../mfc/remote-automation.md)   
 [Ejecución de la automatización remota mediante AUTOCLIK y AUTODRIV](../mfc/running-remote-automation-using-autoclik-and-autodriv.md)

