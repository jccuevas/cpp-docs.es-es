---
title: Comandos estándar | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 943d1bf01890696466638eca3c73839297807fd2
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953127"
---
# <a name="standard-commands"></a>Comandos estándar
El marco de trabajo define muchos mensajes de comando estándar. Normalmente, los identificadores de estos comandos adoptan la forma:  
  
 **ID_** *origen*_*elemento*  
  
 donde *origen* suele ser un nombre de menú y *elemento* es un elemento de menú. Por ejemplo, el identificador de comando para el nuevo comando en el menú archivo es ID_FILE_NEW. Identificadores de comando estándar se muestran en negrita en la documentación. Identificadores definidos por el programador se muestran en una fuente que sea diferente del texto que lo rodea.  
  
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
  
 El marco de trabajo proporciona distintos niveles de compatibilidad para estos comandos. Algunos comandos se admiten únicamente como identificadores de comandos definidos, mientras que otros son compatibles con implementaciones completas. Por ejemplo, el marco de trabajo implementa el comando Abrir en el menú archivo creando un nuevo objeto de documento, mostrar un cuadro de diálogo Abrir y abriendo y leer el archivo. En cambio, debe implementar comandos en el menú Edición, usted mismo, como los comandos como ID_EDIT_COPY dependen de la naturaleza de los datos que va a copiar.  
  
 Para obtener más información acerca de los comandos admitidos y el nivel de implementación suministrado, vea [Nota técnica 22](../mfc/tn022-standard-commands-implementation.md). Los comandos estándares se definen en el archivo AFXRES. H.  
  
## <a name="see-also"></a>Vea también  
 [Objetos de interfaz de usuario e identificadores de comando](../mfc/user-interface-objects-and-command-ids.md)

