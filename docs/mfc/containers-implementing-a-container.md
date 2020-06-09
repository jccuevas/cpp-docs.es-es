---
title: 'Contenedores: Implementar un contenedor'
ms.date: 11/04/2016
helpviewer_keywords:
- applications [OLE], OLE container
- OLE containers [MFC], implementing
ms.assetid: af1e2079-619a-4eac-9327-985ad875823a
ms.openlocfilehash: 0ba8d4aea6b69fdbfeedfba59449d0d30433eb94
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623225"
---
# <a name="containers-implementing-a-container"></a>Contenedores: Implementar un contenedor

En este artículo se resume el procedimiento para implementar un contenedor y se indican otros artículos que proporcionan explicaciones más detalladas sobre la implementación de contenedores. También se enumeran algunas características OLE opcionales que puede que desee implementar y los artículos que describen estas características.

#### <a name="to-prepare-your-cwinapp-derived-class"></a>Para preparar la clase derivada de CWinApp

1. Inicialice las bibliotecas OLE llamando a `AfxOleInit` en la `InitInstance` función miembro.

1. Llame `CDocTemplate::SetContainerInfo` `InitInstance` a en para asignar el menú y los recursos de acelerador usados cuando un elemento incrustado se activa en contexto. Para obtener más información sobre este tema, consulte [activación](activation-cpp.md).

Estas características se proporcionan automáticamente cuando se usa el Asistente para aplicaciones MFC para crear una aplicación contenedora. Vea [crear un programa exe de MFC](reference/mfc-application-wizard.md).

#### <a name="to-prepare-your-view-class"></a>Para preparar la clase de vista

1. Realice un seguimiento de los elementos seleccionados manteniendo un puntero o una lista de punteros si admite la selección múltiple en los elementos seleccionados. La `OnDraw` función debe dibujar todos los elementos OLE.

1. Invalide `IsSelected` para comprobar si el elemento que se le ha pasado está seleccionado actualmente.

1. Implemente un `OnInsertObject` controlador de mensajes para mostrar el cuadro de diálogo **Insertar objeto** .

1. Implemente un `OnSetFocus` controlador de mensajes para transferir el foco de la vista a un elemento OLE incrustado activo en contexto.

1. Implemente un `OnSize` controlador de mensajes para informar a un elemento OLE incrustado que debe cambiar su rectángulo para reflejar el cambio de tamaño de la vista contenedora.

Dado que la implementación de estas características varía drásticamente de una aplicación a la siguiente, el Asistente para aplicaciones solo proporciona una implementación básica. Probablemente tendrá que personalizar estas funciones para que la aplicación funcione correctamente. Para obtener un ejemplo de esto, vea el ejemplo de [contenedor](../overview/visual-cpp-samples.md) .

#### <a name="to-handle-embedded-and-linked-items"></a>Para controlar elementos incrustados y vinculados

1. Derive una clase de [COleClientItem](reference/coleclientitem-class.md). Los objetos de esta clase representan los elementos que se han incrustado en el documento OLE o que están vinculados a él.

1. Reemplace `OnChange` , `OnChangeItemPosition` y `OnGetItemPosition` . Estas funciones controlan el tamaño, la posición y la modificación de elementos incrustados y vinculados.

El Asistente para aplicaciones derivará la clase automáticamente, pero probablemente necesitará invalidar `OnChange` y las demás funciones que se enumeran en el paso 2 del procedimiento anterior. Las implementaciones de esqueleto deben personalizarse para la mayoría de las aplicaciones, ya que estas funciones se implementan de forma diferente de una aplicación a la siguiente. Para obtener ejemplos de esto, vea los ejemplos de MFC [DRAWCLI](../overview/visual-cpp-samples.md) y [Container](../overview/visual-cpp-samples.md).

Debe agregar un número de elementos a la estructura de menús de la aplicación contenedora para admitir OLE. Para obtener más información, vea [menús y recursos: adiciones de contenedor](menus-and-resources-container-additions.md).

También puede que desee admitir algunas de las siguientes características en la aplicación contenedora:

- Activación en contexto al editar un elemento incrustado.

   Para obtener más información, consulte [activación](activation-cpp.md).

- Creación de elementos OLE arrastrando y colocando una selección desde una aplicación de servidor.

   Para obtener más información, vea [arrastrar y colocar de OLE](drag-and-drop-ole.md).

- Vínculos a objetos incrustados o aplicaciones de contenedor/servidor de combinación.

   Para obtener más información, vea [containers: Advanced Features](containers-advanced-features.md).

## <a name="see-also"></a>Consulte también

[Contenedores](containers.md)<br/>
[Contenedores: Elementos de cliente](containers-client-items.md)
