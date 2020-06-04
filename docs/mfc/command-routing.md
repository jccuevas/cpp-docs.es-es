---
title: enrutamiento de comandos
ms.date: 09/06/2019
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- handlers [MFC]
- handlers, command [MFC]
- command routing
ms.assetid: 9393a956-bdd4-47c5-9013-dbd680433f93
ms.openlocfilehash: 8d1e1e59c56439c01655a1416df645ccc6922411
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907626"
---
# <a name="command-routing"></a>enrutamiento de comandos

La responsabilidad de trabajar con comandos se limita a realizar conexiones de mapa de mensajes entre los comandos y sus funciones de controlador, una tarea para la que se usa el [Asistente para clases MFC](reference/mfc-class-wizard.md). También debe escribir el código para los controladores de comandos.

Los mensajes de Windows se envían normalmente a la ventana de marco principal, pero los mensajes de comando se enrutan a otros objetos. El marco de trabajo enruta los comandos a través de una secuencia estándar de objetos de destino del comando, uno de los cuales se espera que tenga un controlador para el comando. Cada objeto de comando-destino comprueba el mapa de mensajes para ver si puede controlar el mensaje entrante.

Distintas clases de comando-destino comprueban sus mapas de mensajes en momentos diferentes. Normalmente, una clase distribuye el comando a otros objetos para darles la primera oportunidad con el comando. Si ninguno de esos objetos controla el comando, la clase original comprueba su propio mapa de mensajes. A continuación, si no puede proporcionar su propio controlador, puede distribuir el comando a todavía más destinos de comando. La siguiente tabla [Ruta estándar de comando](#_core_standard_command_route) muestra cómo cada una de las clases estructura esta secuencia. El orden general en el que un destino de comando enruta un comando es:

1. A su objeto secundario de destino del comando actualmente activo.

1. A sí mismo.

1. A otros destinos de comando.

¿Cuánto cuesta este mecanismo de enrutamiento en comparación con lo que hace el controlador en respuesta a un comando, el costo de enrutamiento es bajo. Tenga en cuenta que el marco de trabajo genera comandos solo cuando el usuario interactúa con un objeto de la interfaz de usuario.

### <a name="_core_standard_command_route"></a> Ruta estándar de comando

|Cuando un objeto de este tipo recibe un comando. . .|Se da a si mismo y a otros objetos de destino del comando una oportunidad de controlar el comando, en este orden:|
|----------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
|Ventana de marco MDI (`CMDIFrameWnd`)|1.  `CMDIChildWnd` activo<br />2.  Esta ventana de marco<br />3.  Aplicación (objeto de `CWinApp`)|
|Ventana de marco de documento (`CFrameWnd`, `CMDIChildWnd`)|1.  Vista activa<br />2.  Esta ventana de marco<br />3.  Aplicación (objeto de `CWinApp`)|
|Ver|1.  Esta vista<br />2.  Documento asociado a la vista|
|Documento|1.  Este documento<br />2.  Plantilla de documento asociada al documento|
|Cuadro de diálogo|1.  Este cuadro de diálogo<br />2.  Ventana propietaria del cuadro de diálogo<br />3.  Aplicación (objeto de `CWinApp`)|

En los casos en los que las entradas numeradas de la segunda columna de la tabla anterior mencionan otros objetos, como un documento, vea el elemento correspondiente de la primera columna. Por ejemplo, cuando lee en la segunda columna que la vista reenvía un comando al documento, vea la entrada “Documento” en la primera columna para seguir el enrutamiento detenidamente.

## <a name="see-also"></a>Vea también

[Cómo el marco llama a un controlador](../mfc/how-the-framework-calls-a-handler.md)
