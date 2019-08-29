---
title: Agregar compatibilidad con ATL a un proyecto MFC
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.adding.atl.mfc
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: b5fe15d6-7752-4818-b9f9-62482ad35c95
ms.openlocfilehash: fba79db013cd9f4cc62ba5826b53e5fa9b15c83a
ms.sourcegitcommit: bf1940a39029dbbd861f95480f55e5e8bd25cda0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108415"
---
# <a name="adding-atl-support-to-your-mfc-project"></a>Agregar compatibilidad con ATL a un proyecto MFC

Si ya ha creado una aplicación basada en MFC, puede Agregar compatibilidad con el Active Template Library (ATL) fácilmente mediante el IDE.

> [!NOTE]
>  Esta compatibilidad solo se aplica a los objetos COM simples que se agregan a un archivo ejecutable de MFC o un proyecto de DLL. Puede agregar otros objetos COM (incluidos los controles ActiveX) a proyectos MFC, pero es posible que los objetos no funcionen según lo esperado.

::: moniker range=">=vs-2019"

1. En Explorador de soluciones, haga clic con el botón secundario en el nodo del proyecto.

1. En el menú contextual, elija **Agregar** y después haga clic en **Nuevo elemento**.

1. Elija **ATL** en el panel izquierdo y, a continuación, elija **compatibilidad con ATL** en el panel central.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-add-atl-support-to-your-mfc-project"></a>Para agregar compatibilidad con ATL a un proyecto MFC

1. En Explorador de soluciones, haga clic con el botón secundario en el nodo del proyecto.

1. En el menú contextual, haga clic en **Agregar** y después en **Agregar clase**.

1. Seleccione **ATL** en el panel izquierdo y, a continuación, elija **Agregar compatibilidad con ATL a un proyecto MFC** en el panel central.

::: moniker-end

Para obtener más información acerca de cómo agregar compatibilidad con ATL cambia el código del proyecto MFC, vea [detalles de la compatibilidad con ATL agregada por el Asistente para ATL](../../mfc/reference/details-of-atl-support-added-by-the-atl-wizard.md)

## <a name="see-also"></a>Vea también

[Agregar una clase](../../ide/adding-a-class-visual-cpp.md)<br/>
[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Agregar una función miembro](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Agregar una variable miembro](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Reemplazar una función virtual](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Controlador de mensajes de MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navegar por la estructura de clases](../../ide/navigate-code-cpp.md)
