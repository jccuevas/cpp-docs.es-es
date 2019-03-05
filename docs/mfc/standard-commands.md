---
title: Comandos estándar
ms.date: 11/04/2016
helpviewer_keywords:
- File menu
- identifiers [MFC], command IDs
- command IDs, standard commands
- OLE commands
- commands [MFC], standard
- standard command IDs
- Window menu commands
- standard commands
- View menu commands
- Edit menu standard commands
- Help [MFC], menus
- programmer-defined IDs [MFC]
ms.assetid: 88cf3ab4-79b3-4ac6-9365-8ac561036fbf
ms.openlocfilehash: 987023322e38584d10901c1ab1fe20ac46926bd2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272092"
---
# <a name="standard-commands"></a>Comandos estándar

El marco de trabajo define muchos mensajes de comando estándar. Normalmente, los identificadores de estos comandos adoptan la forma:

**ID_** *origen*_*elemento*

donde *origen* suele ser un nombre de menú y *elemento* es un elemento de menú. Por ejemplo, el identificador de comando para el nuevo comando en el menú archivo es ID_FILE_NEW. Identificadores de comando estándar se muestran en negrita en la documentación. Identificadores definidos por el programador se muestran en una fuente que sea diferente del texto adyacente.

La siguiente es una lista de algunos de los comandos más importante que admite:

*Comandos del menú archivo*<br/>
Nuevo, abrir, cerrar, guardar, guardar como, Configurar página, el programa de instalación de impresión, impresión, vista previa de impresión, salida y archivos usados recientemente.

*Comandos del menú Edición*<br/>
Borrar, borrar todo, copiar, cortar, buscar, pegar, repetir, reemplazar, seleccionar todo, deshacer y rehacer.

*Comandos del menú Ver*<br/>
Barra de herramientas y barra de estado.

*Comandos del menú Ventana*<br/>
Nueva, organizar, cascada, mosaico Horizontal, mosaico Vertical y dividir.

*Comandos del menú Ayuda*<br/>
Índice, uso de la Ayuda y aproximadamente.

*Comandos OLE (menú Edición)*<br/>
Insertar nuevo objeto, editar vínculos, Pegar vínculo, Pegado especial y *typename* (comandos de verbo) del objeto.

El marco proporciona diferentes niveles de soporte técnico para estos comandos. Algunos comandos se admiten únicamente como identificadores de comandos definidos, mientras que otros son compatibles con implementaciones completas. Por ejemplo, el marco de trabajo implementa el comando Abrir en el menú archivo creando un nuevo objeto de documento, mostrar un cuadro de diálogo Abrir y abrir y leer el archivo. En cambio, debe implementar los comandos en el menú Editar usted mismo, ya que los comandos como ID_EDIT_COPY dependen de la naturaleza de los datos que va a copiar.

Para obtener más información acerca de los comandos admitidos y el nivel de implementación proporcionado, consulte [Nota técnica 22](../mfc/tn022-standard-commands-implementation.md). Los comandos estándar se definen en el archivo AFXRES. H.

## <a name="see-also"></a>Vea también

[Objetos de interfaz de usuario e identificadores de comando](../mfc/user-interface-objects-and-command-ids.md)
