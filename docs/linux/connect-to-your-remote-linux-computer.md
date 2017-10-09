---
title: Conectarse al equipo Linux remoto | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-linux
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
author: BrianPeek
ms.author: brpeek
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: dd817a7d9fad4946cd0aa9f641f9e8f495f1be9a
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

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
