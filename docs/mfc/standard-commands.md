---
title: "Comandos estándar | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bbdb763b2d7da04267a195e5d534da9528f2b74d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="standard-commands"></a>Comandos estándar
El marco de trabajo define muchos mensajes de comando estándar. Normalmente, los identificadores de estos comandos adoptan la forma:  
  
 **ID_** *origen*_*elemento*  
  
 donde *origen* suele ser un nombre de menú y *elemento* es un elemento de menú. Por ejemplo, el identificador de comando para el nuevo comando en el menú archivo es `ID_FILE_NEW`. Identificadores de comando estándar se muestran en negrita en la documentación. Identificadores definidos por el programador se muestran en una fuente que sea diferente del texto que lo rodea.  
  
 La siguiente es una lista de algunos de los comandos más importantes que admite:  
  
 *Comandos del menú archivo*  
 Nuevo, abrir, cerrar, guardar, guardar como, el programa de instalación de la página, el programa de instalación de impresión, imprimir, vista previa de impresión, salida y archivos usados recientemente.  
  
 *Comandos del menú Edición*  
 Borrar, borrar todo, copiar, cortar, buscar, pegar, repetir, reemplazar, seleccionar todo, deshacer y rehacer.  
  
 *Comandos del menú Ver*  
 Barra de herramientas y barra de estado.  
  
 *Comandos del menú Ventana*  
 Nueva, organizar, cascada, mosaico Horizontal, mosaico Vertical y dividir.  
  
 *Comandos del menú Ayuda*  
 Índice, uso de la Ayuda y sobre.  
  
 *Comandos OLE (menú Edición)*  
 Insertar nuevo objeto, editar vínculos, Pegar vínculo, Pegado especial y *typename* objeto (comandos de verbo).  
  
 El marco de trabajo proporciona distintos niveles de compatibilidad para estos comandos. Algunos comandos se admiten únicamente como identificadores de comandos definidos, mientras que otros son compatibles con implementaciones completas. Por ejemplo, el marco de trabajo implementa el comando Abrir en el menú archivo creando un nuevo objeto de documento, mostrar un cuadro de diálogo Abrir y abriendo y leer el archivo. En cambio, debe implementar comandos del menú Edición usted mismo, desde los comandos, como **ID_EDIT_COPY** dependen de la naturaleza de los datos que se va a copiar.  
  
 Para obtener más información acerca de los comandos admitidos y el nivel de implementación suministrado, vea [Nota técnica 22](../mfc/tn022-standard-commands-implementation.md). Los comandos estándares se definen en el archivo AFXRES. H.  
  
## <a name="see-also"></a>Vea también  
 [Objetos de interfaz de usuario e identificadores de comando](../mfc/user-interface-objects-and-command-ids.md)

