---
title: Agregar compatibilidad con ATL a un proyecto MFC
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.adding.atl.mfc
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: b5fe15d6-7752-4818-b9f9-62482ad35c95
ms.openlocfilehash: 9f8861e3b6aa0fee95aa84b989cf1057ae0f76b6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448608"
---
# <a name="adding-atl-support-to-your-mfc-project"></a>Agregar compatibilidad con ATL a un proyecto MFC

Si ya ha creado una aplicación basada en MFC, puede agregar compatibilidad para Active Template Library (ATL) fácilmente mediante la ejecución de agregar compatibilidad de ATL al Asistente para proyectos MFC.

> [!NOTE]
>  ATL y MFC no se admiten con carácter general en las ediciones Express de Visual Studio.

> [!NOTE]
>  Esta compatibilidad solo se aplica a los objetos COM simples que se agregan a un archivo ejecutable de MFC o un proyecto de DLL. Puede agregar otros objetos COM (incluidos los controles ActiveX) a proyectos MFC, pero los objetos podrían no funcionar según lo previsto.

### <a name="to-add-atl-support-to-your-mfc-project"></a>Para agregar compatibilidad con ATL a un proyecto MFC

1. En el Explorador de soluciones, haga clic en el proyecto al que desea agregar compatibilidad con ATL.

1. En el menú contextual, haga clic en **agregar**y, a continuación, haga clic en **Agregar clase**.

1. Seleccione el **agregar compatibilidad con ATL a proyectos MFC** icono.

    > [!NOTE]
    >  Este icono se encuentra en la carpeta ATL la **categorías** panel.

1. Cuando se le solicite, haga clic en **Sí** para agregar compatibilidad con ATL.

Para obtener más información acerca de cómo agregar compatibilidad con ATL cambia el código del proyecto MFC, vea [detalles sobre la compatibilidad agregada por el Asistente para ATL](../../mfc/reference/details-of-atl-support-added-by-the-atl-wizard.md)

## <a name="see-also"></a>Vea también

[Agregar una clase](../../ide/adding-a-class-visual-cpp.md)<br/>
[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Agregar una función miembro](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Agregar una variable miembro](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Reemplazar una función virtual](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Controlador de mensajes de MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navegar por la estructura de clases](../../ide/navigating-the-class-structure-visual-cpp.md)
