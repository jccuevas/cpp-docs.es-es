---
title: 'Contenedores de controles ActiveX: Conectar un Control ActiveX a una Variable de miembro'
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- ActiveX controls [MFC], member variables of project
- connecting ActiveX controls to container member variables
- ActiveX controls [MFC], accessing
- member variables [MFC], ActiveX controls in project
- ActiveX control containers [MFC], ActiveX controls as member variables
ms.assetid: 7898a336-440d-4a60-be43-cb062b807aee
ms.openlocfilehash: c6bc063875f2a31c582c9de32e24e7dfbc7826c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394915"
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>Contenedores de controles ActiveX: Conectar un Control ActiveX a una Variable de miembro

La manera más fácil de obtener acceso a un control ActiveX desde dentro de su aplicación de contenedor de control es asociar el control ActiveX a una variable de miembro de la clase de cuadro de diálogo que contiene el control.

> [!NOTE]
>  Esto no es la única manera de obtener acceso a un control incrustado desde dentro de una clase de contenedor, pero para los fines de este artículo es suficiente.

### <a name="adding-a-member-variable-to-the-dialog-class"></a>Agregar una variable miembro a la clase de cuadro de diálogo

1. Desde la vista de clases, haga clic en la clase de cuadro de diálogo principal para abrir el menú contextual. Por ejemplo: `CContainerDlg`.

1. En el menú contextual, haga clic en **agregar** y, a continuación, **agregar Variable**.

1. En el Asistente para agregar variables miembro, haga clic en **variable de Control**.

1. En el **Id. de Control** cuadro de lista, seleccione el identificador de control del control ActiveX incrustado. Por ejemplo: `IDC_CIRCCTRL1`.

1. En el **nombre de Variable** cuadro, escriba un nombre.

   Por ejemplo, *m_circctl*.

1. Haga clic en **finalizar** para aceptar las opciones seleccionadas y salir del Asistente para agregar variables miembro.

## <a name="see-also"></a>Vea también

[Contenedores de controles ActiveX](../mfc/activex-control-containers.md)
