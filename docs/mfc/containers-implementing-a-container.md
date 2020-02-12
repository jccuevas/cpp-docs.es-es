---
title: 'Contenedores: Implementar un contenedor'
ms.date: 11/04/2016
helpviewer_keywords:
- applications [OLE], OLE container
- OLE containers [MFC], implementing
ms.assetid: af1e2079-619a-4eac-9327-985ad875823a
ms.openlocfilehash: ed95324b8df978a6ab2f7582c0ddf626a45e7fe1
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127925"
---
# <a name="containers-implementing-a-container"></a>Contenedores: Implementar un contenedor

En este artículo se resume el procedimiento para implementar un contenedor y se indican otros artículos que proporcionan explicaciones más detalladas sobre la implementación de contenedores. También se enumeran algunas características OLE opcionales que puede que desee implementar y los artículos que describen estas características.

#### <a name="to-prepare-your-cwinapp-derived-class"></a>Para preparar la clase derivada de CWinApp

1. Inicialice las bibliotecas OLE mediante una llamada a `AfxOleInit` en la función miembro `InitInstance`.

1. Llame a `CDocTemplate::SetContainerInfo` en `InitInstance` para asignar el menú y los recursos de acelerador usados cuando un elemento incrustado se activa en contexto. Para obtener más información sobre este tema, consulte [activación](../mfc/activation-cpp.md).

Estas características se proporcionan automáticamente cuando se usa el Asistente para aplicaciones MFC para crear una aplicación contenedora. Vea [crear un programa exe de MFC](../mfc/reference/mfc-application-wizard.md).

#### <a name="to-prepare-your-view-class"></a>Para preparar la clase de vista

1. Realice un seguimiento de los elementos seleccionados manteniendo un puntero o una lista de punteros si admite la selección múltiple en los elementos seleccionados. La función `OnDraw` debe dibujar todos los elementos OLE.

1. Invalide `IsSelected` para comprobar si el elemento que se le ha pasado está seleccionado actualmente.

1. Implemente un controlador de mensajes de `OnInsertObject` para mostrar el cuadro de diálogo **Insertar objeto** .

1. Implemente un controlador de mensajes `OnSetFocus` para transferir el foco de la vista a un elemento OLE incrustado activo en contexto.

1. Implemente un controlador de mensajes de `OnSize` para informar a un elemento OLE incrustado que debe cambiar su rectángulo para reflejar el cambio de tamaño de la vista que lo contiene.

Dado que la implementación de estas características varía drásticamente de una aplicación a la siguiente, el Asistente para aplicaciones solo proporciona una implementación básica. Probablemente tendrá que personalizar estas funciones para que la aplicación funcione correctamente. Para obtener un ejemplo de esto, vea el ejemplo de [contenedor](../overview/visual-cpp-samples.md) .

#### <a name="to-handle-embedded-and-linked-items"></a>Para controlar elementos incrustados y vinculados

1. Derive una clase de [COleClientItem](../mfc/reference/coleclientitem-class.md). Los objetos de esta clase representan los elementos que se han incrustado en el documento OLE o que están vinculados a él.

1. Invalide `OnChange`, `OnChangeItemPosition`y `OnGetItemPosition`. Estas funciones controlan el tamaño, la posición y la modificación de elementos incrustados y vinculados.

El Asistente para aplicaciones derivará la clase automáticamente, pero probablemente necesitará invalidar `OnChange` y las demás funciones enumeradas en el paso 2 del procedimiento anterior. Las implementaciones de esqueleto deben personalizarse para la mayoría de las aplicaciones, ya que estas funciones se implementan de forma diferente de una aplicación a la siguiente. Para obtener ejemplos de esto, vea los ejemplos de MFC [DRAWCLI](../overview/visual-cpp-samples.md) y [Container](../overview/visual-cpp-samples.md).

Debe agregar un número de elementos a la estructura de menús de la aplicación contenedora para admitir OLE. Para obtener más información, vea [menús y recursos: adiciones de contenedor](../mfc/menus-and-resources-container-additions.md).

También puede que desee admitir algunas de las siguientes características en la aplicación contenedora:

- Activación en contexto al editar un elemento incrustado.

   Para obtener más información, consulte [activación](../mfc/activation-cpp.md).

- Creación de elementos OLE arrastrando y colocando una selección desde una aplicación de servidor.

   Para obtener más información, vea [arrastrar y colocar de OLE](../mfc/drag-and-drop-ole.md).

- Vínculos a objetos incrustados o aplicaciones de contenedor/servidor de combinación.

   Para obtener más información, vea [containers: Advanced Features](../mfc/containers-advanced-features.md).

## <a name="see-also"></a>Consulte también

[Contenedores](../mfc/containers.md)<br/>
[Contenedores: Elementos de cliente](../mfc/containers-client-items.md)
