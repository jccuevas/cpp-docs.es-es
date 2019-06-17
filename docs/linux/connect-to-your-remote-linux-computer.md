---
title: Conexión a un equipo remoto Linux en Visual Studio
description: En este artículo se describe cómo conectarse a una máquina remota Linux desde un proyecto de Visual Studio C++.
ms.date: 06/07/2019
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: 6348681ecc8e6f7863b2119810db24879526a1c6
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821613"
---
# <a name="connect-to-your-remote-linux-computer"></a>Conexión al equipo remoto Linux

::: moniker range="vs-2015"

La compatibilidad con Linux está disponible en Visual Studio 2017 y versiones posteriores.

::: moniker-end

::: moniker range="vs-2019"

Cuando el destino es el subsistema de Windows para Linux (WSL), Visual Studio interactúa con la distribución de Linux directamente a través del sistema de archivos; no es necesaria ninguna conexión remota.

::: moniker-end

Al crear un proyecto de Linux C++ en Visual Studio para un sistema Linux (sea una máquina virtual o un equipo físico), el código se copia en el equipo Linux remoto y, después, se compila según la configuración de Visual Studio. Para configurar esta conexión remota:

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