---
title: Conectarse al equipo Linux remoto | Microsoft Docs
ms.custom: 
ms.date: 11/06/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-linux
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6dce0c1c190854b7927c6e023edd76c9d1cb5645
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2017
---
# <a name="connect-to-your-remote-linux-computer"></a>Conectarse al equipo Linux remoto

Al compilar, el código de Linux se copia en el equipo remoto Linux y, luego, se compila en ese sistema según la configuración elegida en Visual Studio.  Para configurar esta conexión remota:

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
   | **Archivo de clave privada**    | Clave privada creada para la conexión ssh
   | **Frase de contraseña**          | Frase de contraseña usada con la clave privada seleccionada anteriormente

1. Haga clic en el botón **Conectar** para intentar la conexión con el equipo remoto.  Si se produce un error en la conexión, se marcan en rojo los cuadros de entrada que deben cambiarse.

   ![Error del Administrador de conexiones](media/settings_connectionmanagererror.png)