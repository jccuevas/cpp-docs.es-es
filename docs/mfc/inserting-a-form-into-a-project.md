---
title: Insertar un formulario en un proyecto
ms.date: 11/04/2016
helpviewer_keywords:
- inserting forms [MFC]
- Insert New dialog box [MFC]
- forms, adding to projects
ms.assetid: f3bd2998-3ce2-496d-ac5c-57ca70eec7cb
ms.openlocfilehash: 8e3162ac3917781920130bcbed23864eb90afa59
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618427"
---
# <a name="inserting-a-form-into-a-project"></a>Insertar un formulario en un proyecto

Los formularios proporcionan un contenedor práctico para los controles. Puede insertar fácilmente un formulario basado en MFC en la aplicación siempre y cuando la aplicación admita las bibliotecas MFC.

### <a name="to-insert-a-form-into-your-project"></a>Para insertar un formulario en el proyecto

1. En Vista de clases, seleccione el proyecto al que desea agregar el formulario y haga clic con el botón secundario del mouse.

1. En el menú contextual, haga clic en **Agregar** y después en **Agregar clase**.

   Si el comando **nuevo formulario** no está disponible, el proyecto puede basarse en el Active Template Library (ATL). Para agregar un formulario a un proyecto ATL, debe [especificar ciertos valores de configuración](../atl/reference/application-settings-atl-project-wizard.md) al crear el proyecto por primera vez.

1. En la carpeta **MFC** , haga clic en **clase MFC**.

1. Mediante el Asistente para clases MFC, haga que la nueva clase se derive de [CFormView](reference/cformview-class.md).

Visual C++ agrega el formulario a la aplicación y lo abre en el editor de cuadros de diálogo para que pueda empezar a agregar controles y trabajar en su diseño global.

Es posible que desee realizar los siguientes pasos adicionales (no aplicables a las aplicaciones basadas en cuadros de diálogo):

1. Invalide la `OnUpdate` función miembro.

1. Implemente una función miembro para trasladar los datos de la vista al documento.

1. Cree una `OnPrint` función miembro.

## <a name="see-also"></a>Consulte también

[Vistas de formulario](form-views-mfc.md)
