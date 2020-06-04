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
ms.openlocfilehash: 620a9ec58b3a5a8fcdac63626b81fbc4620de399
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371621"
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>Contenedores de controles ActiveX: Conectar un control ActiveX a una variable de miembro

La forma más fácil de tener acceso a un control ActiveX desde su aplicación contenedora de control es asociar el control ActiveX con una variable miembro de la clase de cuadro de diálogo que contendrá el control.

> [!NOTE]
> Esta no es la única manera de tener acceso a un control incrustado desde dentro de una clase contenedora, pero para los fines de este artículo es suficiente.

### <a name="adding-a-member-variable-to-the-dialog-class"></a>Agregar una variable miembro a la clase de cuadro de diálogo

1. En la vista de clases, haga clic con el botón derecho en la clase de cuadro de diálogo principal para abrir el menú contextual. Por ejemplo, `CContainerDlg`.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, en **Agregar variable**.

1. En el Asistente para agregar variables miembro, haga clic en Variable de **control**.

1. En el cuadro de lista **ID** de control, seleccione el identificador de control del control ActiveX incrustado. Por ejemplo, `IDC_CIRCCTRL1`.

1. En el cuadro **Nombre de variable,** escriba un nombre.

   Por ejemplo, *m_circctl*.

1. Haga clic en **Finalizar** para aceptar sus opciones y salir del Asistente para agregar variables miembro.

## <a name="see-also"></a>Consulte también

[Contenedores de controles ActiveX](../mfc/activex-control-containers.md)
