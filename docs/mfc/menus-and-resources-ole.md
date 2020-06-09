---
title: Menús y recursos (OLE)
ms.date: 11/04/2016
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
ms.openlocfilehash: e705f28476df7b594f9648aee8317759211c66c9
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626209"
---
# <a name="menus-and-resources-ole"></a>Menús y recursos (OLE)

Este grupo de artículos explica el uso de menús y recursos en aplicaciones de documentos OLE de MFC.

La edición visual OLE coloca requisitos adicionales en el menú y otros recursos proporcionados por las aplicaciones de documentos OLE, ya que hay una serie de modos en los que se pueden iniciar y usar las aplicaciones de contenedor y servidor (componente). Por ejemplo, una aplicación de servidor completo puede ejecutarse en cualquiera de estos tres modos:

- Independiente.

- En contexto, para editar un elemento en el contexto de un contenedor.

- Abrir, para editar un elemento fuera del contexto de su contenedor, a menudo en una ventana independiente.

Esto requiere tres diseños de menú independientes, uno para cada modo posible de la aplicación. Las tablas de aceleradores también son necesarias para cada nuevo modo. Una aplicación contenedora puede admitir o no la activación en contexto; Si lo hace, necesita una nueva estructura de menú y las tablas de acelerador asociadas.

La activación en contexto requiere que las aplicaciones de contenedor y servidor deban negociar el espacio de la barra de menús, barras de herramientas y estado. Todos los recursos deben diseñarse teniendo esto en cuenta. En el artículo [menús y recursos: la combinación de menús](menus-and-resources-menu-merging.md) trata este tema en detalle.

Debido a estos problemas, las aplicaciones de documentos OLE creadas con el Asistente para aplicaciones pueden tener hasta cuatro menús independientes y recursos de tabla de aceleradores. Se usan por los siguientes motivos:

|Nombre del recurso|Uso|
|-------------------|---------|
|IDR_MAINFRAME|Se utiliza en una aplicación MDI si no hay ningún archivo abierto o en una aplicación SDI, independientemente de los archivos abiertos. Este es el menú estándar que se usa en aplicaciones que no son de OLE.|
|tipo de IDR_ \<project>|Se utiliza en una aplicación MDI si los archivos están abiertos. Se usa cuando una aplicación se ejecuta de manera independiente. Este es el menú estándar que se usa en aplicaciones que no son de OLE.|
|IDR_ \<project> TYPE_SRVR_IP|Lo usa el servidor o el contenedor cuando un objeto está abierto en su lugar.|
|IDR_ \<project> TYPE_SRVR_EMB|Lo usa una aplicación de servidor si se abre un objeto sin usar la activación en contexto.|

Cada uno de estos nombres de recurso representa un menú y, normalmente, una tabla de aceleradores. Se debe usar un esquema similar en aplicaciones MFC que no se crean con el Asistente para aplicaciones.

En los artículos siguientes se describen los temas relacionados con los contenedores, los servidores y la combinación de menús necesaria para implementar la activación en contexto:

- [Menús y recursos: Adiciones de contenedor](menus-and-resources-container-additions.md)

- [Menús y recursos: Adiciones de servidor](menus-and-resources-server-additions.md)

- [Menús y recursos: Combinación de menús](menus-and-resources-menu-merging.md)

## <a name="see-also"></a>Consulte también

[OLE](ole-in-mfc.md)
