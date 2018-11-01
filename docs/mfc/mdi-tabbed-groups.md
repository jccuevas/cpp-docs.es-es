---
title: Grupos con pestañas MDI
ms.date: 11/04/2016
helpviewer_keywords:
- mdi [MFC], tabbed groups
- tabbed grous [MFC]
ms.assetid: 0a464f36-39b7-4e68-8b67-ec175de28377
ms.openlocfilehash: cefd97b377c2755b158830d8e649ac40f90fee11
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544500"
---
# <a name="mdi-tabbed-groups"></a>Grupos con pestañas MDI

La característica de grupos con fichas de varios documentos MDI (interfaz) permite que varias aplicaciones de MDI (interfaz) del documento mostrar una o varias ventanas con pestañas (o grupos de ventanas con pestañas, conocidos como *grupos con pestañas*) en el área de cliente MDI. Las ventanas con pestañas se pueden alinear horizontal o verticalmente. Si una aplicación hospeda más de un grupo de pestañas de MDI, los grupos se separan mediante separadores.

## <a name="features"></a>Características

Éstas son las características de los grupos con pestañas de MDI:

- Una aplicación puede crear ventanas con pestañas dinámicamente.

- Una aplicación puede alinear ventanas con pestañas horizontal o verticalmente.

- Grupos de ventanas con pestañas se separan mediante separadores. El usuario puede cambiar el tamaño de grupos con fichas mediante el uso del divisor.

- El usuario puede arrastrar fichas individuales entre grupos.

- El usuario puede arrastrar las fichas individuales para crear grupos nuevos.

- El usuario puede mover las pestañas o crear nuevos grupos mediante el uso de un menú contextual.

- Una aplicación puede guardar y cargar el diseño de ventanas con pestañas.

- Una aplicación puede guardar y cargar la lista de documentos MDI.

- Una aplicación puede tener acceso a grupos con fichas individuales y modificar sus parámetros.

### <a name="using-mdi-tabbed-groups"></a>Grupos con pestañas MDI de uso

Las siguientes tareas se realizan normalmente con los grupos de pestañas de MDI son:

- Para habilitar los grupos de una ventana de marco principal MDI con fichas, llame a [CMDIFrameWndEx:: Enablemditabbedgroups](../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups). El segundo parámetro de este método es una instancia de la `CMDITabInfo` clase. Puede usar los parámetros predeterminados o modificarlos antes de llamar a `CMDIFrameWndEx::EnableMDITabbedGroups`.

- Para modificar las propiedades de un grupo de pestañas de MDI en tiempo de ejecución, crear o modificar un `CMDITabInfo` objeto y llamar a `CMDIFrameWndEx::EnableMDITabbedGroups` nuevo

- Para obtener una lista de MDI con fichas en windows, llame a `CMDIFrameWndEx::GetMDITabGroups`.

- Para crear un nuevo grupo con pestañas MDI junto a un grupo con pestañas activo, llame a `CMDIFrameWndEx::MDITabNewGroup`.

- Para desplazar el foco de entrada a la ventana anterior o siguiente de un grupo con pestañas, llame a `CMDIFrameWndEx::MDITabMoveToNextGroup`.

- Para determinar si una ventana es un miembro de los formularios MDI con fichas llamada grupo `CMDIFrameWndEx::IsMemberOfMDITabGroup`.

- Para determinar si están habilitados las pestañas MDI o grupos con pestañas de MDI de una ventana de marco principal, llame a `CMDIFrameWndEx::AreMDITabs`. Para determinar solo si están habilitados los grupos con pestañas de MDI, llame a `CMDIFrameWndEx::IsMDITabbedGroup`.

- Para mostrar un menú contextual cuando el usuario hace clic en una pestaña o lo arrastra a otro grupo de pestañas de MDI, invalidar `CMDIFrameWndEx::OnShowMDITabContextMenu` en el `CMDIFrameWndEx`-clase derivada. Si no implementa este método, la aplicación no mostrará el menú contextual.

- Para guardar el diseño de los grupos con pestañas de MDI en una aplicación, llame a `CMDIFrameWndEx::SaveMDIState`. Para cargar una guardado previamente MDI con fichas perfil de grupo, llame a `CMDIFrameWndEx::LoadMDIState`. También puede llamar a estos métodos para cargar o guardar la lista de los documentos abiertos en una aplicación MDI. Para obtener más información sobre cómo guardar y cargar el estado MDI, consulte [CMDIFrameWndEx::LoadMDIState](../mfc/reference/cmdiframewndex-class.md#loadmdistate).

## <a name="see-also"></a>Vea también

[Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)<br/>
[CMDIFrameWndEx (clase)](../mfc/reference/cmdiframewndex-class.md)<br/>
[CMDIChildWndEx (clase)](../mfc/reference/cmdichildwndex-class.md)<br/>
[CMDITabInfo (clase)](../mfc/reference/cmditabinfo-class.md)
