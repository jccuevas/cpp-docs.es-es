---
title: 'Contenedores de controles ActiveX: Conectar un control ActiveX a una variable de miembro'
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- ActiveX controls [MFC], member variables of project
- connecting ActiveX controls to container member variables
- ActiveX controls [MFC], accessing
- member variables [MFC], ActiveX controls in project
- ActiveX control containers [MFC], ActiveX controls as member variables
ms.assetid: 7898a336-440d-4a60-be43-cb062b807aee
ms.openlocfilehash: 87cb560a1054a912a4e8574cfe2dee74d5e61fe6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625130"
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>Contenedores de controles ActiveX: Conectar un control ActiveX a una variable de miembro

La forma más fácil de tener acceso a un control ActiveX desde la aplicación de contenedor de control consiste en asociar el control ActiveX a una variable miembro de la clase de cuadro de diálogo que contendrá el control.

> [!NOTE]
> Esta no es la única manera de tener acceso a un control incrustado desde dentro de una clase de contenedor, pero para los fines de este artículo es suficiente.

### <a name="adding-a-member-variable-to-the-dialog-class"></a>Agregar una variable miembro a la clase de cuadro de diálogo

1. En Vista de clases, haga clic con el botón secundario en la clase de cuadro de diálogo principal para abrir el menú contextual. Por ejemplo, `CContainerDlg`.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, en **Agregar variable**.

1. En el Asistente para agregar variables miembro, haga clic en **variable de control**.

1. En el cuadro de lista ID. de **control** , seleccione el ID. de control del control ActiveX incrustado. Por ejemplo, `IDC_CIRCCTRL1`.

1. En el cuadro **nombre de variable** , escriba un nombre.

   Por ejemplo, *m_circctl*.

1. Haga clic en **Finalizar** para aceptar las opciones y salir del Asistente para agregar variables miembro.

## <a name="see-also"></a>Consulte también

[Contenedores de controles ActiveX](activex-control-containers.md)
