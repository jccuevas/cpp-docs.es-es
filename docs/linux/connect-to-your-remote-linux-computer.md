---
title: Conexión a un equipo remoto Linux en Visual Studio
description: En este artículo se describe cómo conectarse a una máquina remota Linux desde un proyecto de Visual Studio C++.
ms.date: 07/20/2018
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: ce6a3c02846586dbc46b0c9bc0db0d579878c814
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575248"
---
# <a name="connect-to-your-remote-linux-computer"></a>Conectarse al equipo Linux remoto

Al crear un proyecto de Linux C++ en Visual Studio, el código se copia al equipo Linux remoto y, después, se compila según la configuración de Visual Studio. Para configurar esta conexión remota:

1. Compile el proyecto por primera vez o cree manualmente una nueva entrada al seleccionar **Herramientas > Opciones** y, luego, abrir el nodo **Multiplataforma > Administrador de conexiones** y hacer clic en el botón **Agregar**.

   ![Administrador de conexiones](media/settings_connectionmanager.png)

   En cualquier caso, aparecerá la ventana **Conectar con el sistema remoto**.

   ![Conectar con el sistema remoto](media/connect.png)

1. Especifique la siguiente información:

   | Entrada | Descripción
   | ----- | ---
   | **Nombre de host**           | Nombre o dirección IP del dispositivo de destino
   | **Puerto**                | Puerto en el que se ejecuta el servicio SSH, normalmente 22
   | **Nombre de usuario**           | Usuario como el que se autentica
   | **Tipo de autenticación** | Se admite contraseña o clave privada
   | **Contraseña**            | Contraseña para el nombre de usuario especificado
   | **Archivo de clave privada**    | Archivo de clave privada creado para la conexión ssh
   | **Frase de contraseña**          | Frase de contraseña usada con la clave privada seleccionada anteriormente

1. Haga clic en el botón **Conectar** para intentar la conexión con el equipo remoto.  Si se produce un error en la conexión, se marcan en rojo los cuadros de entrada que deben cambiarse.

   ![Error del Administrador de conexiones](media/settings_connectionmanagererror.png)