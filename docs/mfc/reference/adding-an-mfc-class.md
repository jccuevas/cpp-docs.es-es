---
title: Agregar una clase MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.classes.adding.mfc
dev_langs:
- C++
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes
ms.assetid: 9a96b67f-40bf-43d4-8872-2f8dfc5404f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 86e42ab5c2e8e15f5f56687b5ca99d160270017b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436369"
---
# <a name="adding-an-mfc-class"></a>Agregar una clase MFC

Para agregar las clases derivadas de clases de la biblioteca Microsoft Foundation Class (MFC) a su proyecto, use el **Agregar clase** comando disponible en [vista de clases](/visualstudio/ide/viewing-the-structure-of-code). Especifique el nombre de la nueva clase, seleccione la clase base y seleccione el identificador del cuadro de diálogo con el que está asociado (si existe). El Asistente de código crea un archivo de encabezado y un archivo de implementación y los agrega al proyecto.

> [!NOTE]
>  Puede agregar clases MFC a una aplicación de COM de ATL si inicialmente [creó la aplicación con compatibilidad con MFC](../../atl/reference/mfc-support-in-atl-projects.md). También puede agregar clases MFC a proyectos de Win32 que tienen compatibilidad con MFC.

### <a name="to-add-an-mfc-class-to-your-project"></a>Para agregar una clase MFC al proyecto

1. Desde la vista de clases, haga clic en el nombre del proyecto. Haga clic en **agregar** y, a continuación, haga clic en **Agregar clase** para abrir el [Agregar clase](../../ide/add-class-dialog-box.md) cuadro de diálogo.

1. En el panel Plantillas, seleccione **clase MFC** y presione la **agregar** botón.

1. Definir la configuración de la nueva clase en el [Asistente para clases MFC](../../mfc/reference/mfc-add-class-wizard.md) cuadro de diálogo.

1. Haga clic en **finalizar** para cerrar el asistente y ver la nueva clase en la vista de clases. También puede ver los archivos creados por el Asistente en **el Explorador de soluciones**.

## <a name="see-also"></a>Vea también

[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Agregar una clase](../../ide/adding-a-class-visual-cpp.md)<br/>
[Información general de clases](../../mfc/class-library-overview.md)

