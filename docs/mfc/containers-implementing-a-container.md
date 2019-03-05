---
title: 'Contenedores: Implementación de un contenedor'
ms.date: 11/04/2016
helpviewer_keywords:
- applications [OLE], OLE container
- OLE containers [MFC], implementing
ms.assetid: af1e2079-619a-4eac-9327-985ad875823a
ms.openlocfilehash: 0ab91316c9ee07296fbc46f9f17b3c46c71ee96f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271429"
---
# <a name="containers-implementing-a-container"></a>Contenedores: Implementación de un contenedor

En este artículo se resume el procedimiento para implementar un contenedor y se apunta a otros artículos que proporcionan más explicaciones acerca de cómo implementar contenedores. También se enumeran algunas características OLE opcionales que desea implementar y los artículos que describen estas características.

#### <a name="to-prepare-your-cwinapp-derived-class"></a>Para preparar la clase derivada de CWinApp

1. Inicializar las bibliotecas OLE mediante una llamada a `AfxOleInit` en el `InitInstance` función miembro.

1. Llame a `CDocTemplate::SetContainerInfo` en `InitInstance` para asignar el menú y el Acelerador de recursos que se utiliza cuando un elemento incrustado es activar en contexto. Para obtener más información sobre este tema, consulte [activación](../mfc/activation-cpp.md).

Estas características se proporcionan automáticamente cuando se usa el Asistente para aplicaciones MFC para crear una aplicación contenedora. Consulte [crear un programa EXE de MFC](../mfc/reference/mfc-application-wizard.md).

#### <a name="to-prepare-your-view-class"></a>Para preparar la clase de vista

1. Realizar un seguimiento de los elementos seleccionados al mantener el puntero o su propia lista de punteros si admite selección múltiple, los elementos seleccionados. Su `OnDraw` función debe dibujar todos los elementos OLE.

1. Invalidar `IsSelected` para comprobar si el elemento pasado a la está seleccionado actualmente.

1. Implemente un `OnInsertObject` controlador de mensajes para mostrar el **Insertar objeto** cuadro de diálogo.

1. Implemente un `OnSetFocus` controlador para transferir el foco de la vista a OLE en contexto activo incrustar el elemento de mensaje.

1. Implemente un `OnSize` controlador de mensajes para informar a OLE incrustados elemento que debe cambiar el rectángulo para reflejar el cambio de tamaño de la vista contenedora.

Dado que la implementación de estas características varía considerablemente de una aplicación a la siguiente, el Asistente para aplicaciones proporciona solo una implementación básica. Probablemente tendrá que personalizar estas funciones para que la aplicación funcione correctamente. Para obtener un ejemplo de esto, consulte el [contenedor](../visual-cpp-samples.md) ejemplo.

#### <a name="to-handle-embedded-and-linked-items"></a>Para controlar los elementos vinculados e incrustados

1. Derive una clase de [COleClientItem](../mfc/reference/coleclientitem-class.md). Los objetos de esta clase representan los elementos que se han incrustado en o vinculado a su documento OLE.

1. Invalidar `OnChange`, `OnChangeItemPosition`, y `OnGetItemPosition`. Estas funciones controlan el ajuste de tamaño, posición y la modificación de elementos vinculados e incrustados.

El Asistente para aplicaciones derivará la clase para usted, pero es probable que deba reemplazar `OnChange` y las demás funciones mostradas con ella en el paso 2 del procedimiento anterior. Las implementaciones de esqueleto deben personalizarse para la mayoría de las aplicaciones, ya que estas funciones se implementan de forma diferente de una aplicación a la siguiente. Para obtener ejemplos de esto, consulte los ejemplos MFC [DRAWCLI](../visual-cpp-samples.md) y [contenedor](../visual-cpp-samples.md).

Debe agregar un número de elementos a la estructura de menús de la aplicación contenedora para admitir OLE. Para obtener más información, consulte [menús y recursos: Adiciones de contenedor](../mfc/menus-and-resources-container-additions.md).

También puede admitir algunas de las siguientes características en la aplicación de contenedor:

- Activación en contexto al editar un elemento incrustado.

   Para obtener más información, consulte [activación](../mfc/activation-cpp.md).

- Creación de elementos OLE arrastrando y colocando una selección de una aplicación de servidor.

   Para obtener más información, consulte [arrastrar y colocar (OLE)](../mfc/drag-and-drop-ole.md).

- Vínculos a objetos incrustados o aplicaciones de servidor/contenedor de combinación.

   Para obtener más información, consulte [contenedores: Características avanzadas](../mfc/containers-advanced-features.md).

## <a name="see-also"></a>Vea también

[Contenedores](../mfc/containers.md)<br/>
[Contenedores: Elementos de cliente](../mfc/containers-client-items.md)
