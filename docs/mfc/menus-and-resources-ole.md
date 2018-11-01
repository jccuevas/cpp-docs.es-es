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
ms.openlocfilehash: 8b8e278564c2c293cabfcd56ab9ce2cdb4807e19
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511740"
---
# <a name="menus-and-resources-ole"></a>Menús y recursos (OLE)

Este grupo de artículos explica el uso de menús y recursos en aplicaciones de documentos OLE de MFC.

Edición visual OLE impone requisitos adicionales en el menú y otros recursos proporcionados por aplicaciones de documentos OLE porque hay una serie de modos de en qué contenedor ambos y se pueden iniciar y usar aplicaciones de servidor (componente). Por ejemplo, puede ejecutar una aplicación de servidor completo en cualquiera de estos tres modos:

- Actuar por sí sola.

- En su lugar, para editar un elemento dentro del contexto de un contenedor.

- Abrir para editar un elemento fuera del contexto de su contenedor, a menudo en una ventana independiente.

Esto requiere tres diseños de menú diferentes, uno para cada posible modo de la aplicación. Tablas de aceleradores también son necesarias para cada modo. Una aplicación contenedora puede o no puede admitir la activación en contexto; Si es así, necesita una nueva estructura de menú y tablas de aceleradores asociadas.

Activación en contexto requiere que las aplicaciones de contenedor y servidor negocien el espacio de la barra de menú, barra de herramientas y el estado. Todos los recursos deben diseñarse teniendo esto en mente. El artículo [menús y recursos: combinación de menús](../mfc/menus-and-resources-menu-merging.md) se tratan en este tema en detalle.

Debido a estos problemas, las aplicaciones de documento OLE creadas con el Asistente para la aplicación pueden tener hasta cuatro menús independientes y recursos de la tabla de aceleradores. Se utilizan por las razones siguientes:

|Nombre del recurso|Usar|
|-------------------|---------|
|IDR_MAINFRAME|Se utiliza en una aplicación MDI si ningún archivo está abierto o en una aplicación SDI, independientemente de los archivos abiertos. Se trata de un menú estándar utilizado en aplicaciones que no son compatibles con OLE.|
|IDR_\<proyecto > tipo|Se utiliza en una aplicación MDI si los archivos están abiertos. Se utiliza cuando se ejecuta una aplicación independiente. Se trata de un menú estándar utilizado en aplicaciones que no son compatibles con OLE.|
|IDR_\<proyecto > TYPE_SRVR_IP|Usa el servidor o contenedor cuando se abre un objeto en su lugar.|
|IDR_\<proyecto > TYPE_SRVR_EMB|Usa una aplicación de servidor si se abre un objeto sin usar activación en contexto.|

Cada uno de estos nombres de recursos representa un menú y, por lo general, una tabla de aceleradores. Un esquema similar debe usarse en aplicaciones MFC que no se crean con el Asistente para la aplicación.

Los siguientes artículos describen temas relacionados con la combinación necesarios para implementar la activación en contexto de menús, servidores y contenedores:

- [Menús y recursos: Adiciones de contenedor](../mfc/menus-and-resources-container-additions.md)

- [Menús y recursos: Adiciones de servidor](../mfc/menus-and-resources-server-additions.md)

- [Menús y recursos: Combinación de menús](../mfc/menus-and-resources-menu-merging.md)

## <a name="see-also"></a>Vea también

[OLE](../mfc/ole-in-mfc.md)

