---
title: Grupos con pestañas MDI
ms.date: 11/04/2016
helpviewer_keywords:
- mdi [MFC], tabbed groups
- tabbed grous [MFC]
ms.assetid: 0a464f36-39b7-4e68-8b67-ec175de28377
ms.openlocfilehash: 0c1bf925003d5081b2cdc837012a57585b1ace60
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624355"
---
# <a name="mdi-tabbed-groups"></a>Grupos con pestañas MDI

La característica de grupos con pestañas de la interfaz de múltiples documentos (MDI) permite que las aplicaciones de interfaz de múltiples documentos (MDI) muestren una o varias ventanas con pestañas (o grupos de ventanas con pestañas, conocidas como *grupos con pestañas*) en el área cliente de MDI. Las ventanas con pestañas se pueden alinear vertical u horizontalmente. Si una aplicación hospeda más de un grupo con pestañas MDI, los grupos se separan mediante separadores.

## <a name="features"></a>Características

A continuación se muestran las características de los grupos con pestañas MDI:

- Una aplicación puede crear ventanas con pestañas dinámicamente.

- Una aplicación puede alinear las ventanas con pestañas horizontal o verticalmente.

- Los grupos de ventanas con pestañas se separan mediante separadores. El usuario puede cambiar el tamaño de los grupos con pestañas mediante el divisor.

- El usuario puede arrastrar pestañas individuales entre grupos.

- El usuario puede arrastrar pestañas individuales para crear nuevos grupos.

- El usuario puede quitar pestañas o crear nuevos grupos mediante un menú contextual.

- Una aplicación puede guardar y cargar el diseño de las ventanas con pestañas.

- Una aplicación puede guardar y cargar la lista de documentos MDI.

- Una aplicación puede tener acceso a grupos con pestañas individuales y modificar sus parámetros.

### <a name="using-mdi-tabbed-groups"></a>Usar grupos con pestañas MDI

A continuación se indican las tareas que se suelen realizar con los grupos con pestañas MDI:

- Para habilitar los grupos con pestañas MDI en una ventana de marco principal, llame a [cmdiframewndex (:: EnableMDITabbedGroups](reference/cmdiframewndex-class.md#enablemditabbedgroups). El segundo parámetro de este método es una instancia de la `CMDITabInfo` clase. Puede usar los parámetros predeterminados o modificarlos antes de llamar a `CMDIFrameWndEx::EnableMDITabbedGroups` .

- Para modificar las propiedades de un grupo con pestañas MDI en tiempo de ejecución, cree o modifique un `CMDITabInfo` objeto y vuelva a llamar a. `CMDIFrameWndEx::EnableMDITabbedGroups`

- Para obtener una lista de ventanas con pestañas MDI, llame a `CMDIFrameWndEx::GetMDITabGroups` .

- Para crear un nuevo grupo con pestañas MDI junto a un grupo de pestañas activo, llame a `CMDIFrameWndEx::MDITabNewGroup` .

- Para desplazar el foco de entrada a la ventana anterior o siguiente de un grupo con pestañas, llame a `CMDIFrameWndEx::MDITabMoveToNextGroup` .

- Para determinar si una ventana es miembro de una llamada de grupo con pestañas MDI `CMDIFrameWndEx::IsMemberOfMDITabGroup` .

- Para determinar si las pestañas MDI o los grupos con pestañas MDI están habilitados para una ventana de marco principal, llame a `CMDIFrameWndEx::AreMDITabs` . Para determinar solo si los grupos con pestañas MDI están habilitados, llame a `CMDIFrameWndEx::IsMDITabbedGroup` .

- Para mostrar un menú contextual cuando el usuario hace clic en una ficha o la arrastra a otro grupo con pestañas MDI, invalide `CMDIFrameWndEx::OnShowMDITabContextMenu` en la `CMDIFrameWndEx` clase derivada de. Si no implementa este método, la aplicación no mostrará el menú contextual.

- Para guardar el diseño de los grupos con pestañas MDI en una aplicación, llame a `CMDIFrameWndEx::SaveMDIState` . Para cargar un perfil de grupo con pestañas MDI guardado previamente, llame a `CMDIFrameWndEx::LoadMDIState` . También puede llamar a estos métodos para cargar o guardar la lista de documentos abiertos en una aplicación MDI. Para obtener más información sobre cómo guardar y cargar el estado de MDI, vea [cmdiframewndex (:: LoadMDIState](reference/cmdiframewndex-class.md#loadmdistate).

## <a name="see-also"></a>Consulte también

[Elementos de la interfaz de usuario](user-interface-elements-mfc.md)<br/>
[Clase Cmdiframewndex (](reference/cmdiframewndex-class.md)<br/>
[Clase Cmdichildwndex (](reference/cmdichildwndex-class.md)<br/>
[CMDITabInfo (clase)](reference/cmditabinfo-class.md)
