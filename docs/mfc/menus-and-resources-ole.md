---
title: Menús y recursos (OLE) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE visual editing servers [MFC]
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- string tables [MFC], visual editing applications
- OLE containers [MFC], menus and resources
- OLE applications [MFC], menus and resources
- OLE server applications [MFC], menus and resources
- toolbars [MFC], OLE document applications
- string editing [MFC], visual editing applications
- server applications [MFC], OLE menus and resources
- applications [OLE], menus and resources
- menus [MFC], OLE document applications
- in-place activation [MFC], OLE menus and resources
- containers [MFC], OLE container applications
- OLE menus and resources [MFC]
ms.assetid: 52bfa086-7d3d-466f-94c7-c7061f3bdb3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 54cc874fd3c95123446ab81b920bfe0fce52df5e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347099"
---
# <a name="menus-and-resources-ole"></a>Menús y recursos (OLE)
Este grupo de artículos explica el uso de menús y recursos en aplicaciones de documentos OLE de MFC.  
  
 Edición visual OLE impone requisitos adicionales en el menú y otros recursos proporcionados por aplicaciones de documentos OLE porque hay una serie de modos en que ambas contenedor y se pueden iniciar y usar las aplicaciones de servidor (componente). Por ejemplo, puede ejecutar una aplicación de servidor completo en cualquiera de estos tres modos:  
  
-   Actuar por sí sola.  
  
-   En su lugar, para editar un elemento en el contexto de un contenedor.  
  
-   Abrir para editar un elemento fuera del contexto de su contenedor, a menudo, en una ventana independiente.  
  
 Esto requiere tres diseños de menú diferentes, uno para cada modo posible de la aplicación. Tablas de aceleradores también son necesarias para cada modo de nuevo. Una aplicación de contenedor puede o no admitir la activación en contexto; Si es así, se necesita una nueva estructura de menú y tablas de aceleradores asociadas.  
  
 Activación en contexto requiere que las aplicaciones de contenedor y servidor negocien el espacio de la barra de menú, barra de herramientas y el estado. Todos los recursos deben diseñarse con esto en mente. El artículo [menús y recursos: combinación de menús](../mfc/menus-and-resources-menu-merging.md) trata este tema en detalle.  
  
 Debido a estos problemas, aplicaciones de documentos OLE creadas con el Asistente para aplicaciones pueden tener hasta cuatro menús independientes y recursos de la tabla de aceleradores. Se utilizan por las razones siguientes:  
  
|Nombre del recurso|Usar|  
|-------------------|---------|  
|**IDR_MAINFRAME**|Utilizar en una aplicación MDI si ningún archivo está abierto, o en una aplicación SDI, independientemente de los archivos abiertos. Este es el menú estándar que se utiliza en aplicaciones no compatibles con OLE.|  
|**IDR_\<proyecto > tipo**|Se utiliza en una aplicación MDI si hay archivos abiertos. Se utiliza cuando se ejecuta una aplicación independiente. Este es el menú estándar que se utiliza en aplicaciones no compatibles con OLE.|  
|**IDR_\<proyecto > TYPE_SRVR_IP**|Utilizado por el servidor o contenedor cuando se abre un objeto en su lugar.|  
|**IDR_\<proyecto > TYPE_SRVR_EMB**|Usar una aplicación de servidor si se abre un objeto sin usar la activación en contexto.|  
  
 Cada uno de estos nombres de recursos representa un menú y, por lo general, una tabla de aceleradores. Debe utilizarse un esquema similar en las aplicaciones MFC que no se crean con el Asistente para aplicaciones.  
  
 Los artículos siguientes tratan temas relacionados con contenedores, servidores y la combinación de menús necesarios para implementar la activación en contexto:  
  
-   [Menús y recursos: Adiciones de contenedor](../mfc/menus-and-resources-container-additions.md)  
  
-   [Menús y recursos: Adiciones de servidor](../mfc/menus-and-resources-server-additions.md)  
  
-   [Menús y recursos: Combinación de menús](../mfc/menus-and-resources-menu-merging.md)  
  
## <a name="see-also"></a>Vea también  
 [OLE](../mfc/ole-in-mfc.md)

