---
title: Implementación de un cuadro de diálogo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CSimpleDialog class, implementing dialog boxes in ATL
- dialog boxes, ATL
- CAxDialogImpl class, implementing dialog boxes in ATL
- ATL, dialog boxes
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b656af864f8a0dd7c5a69866976b4c1e624b87b9
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764298"
---
# <a name="implementing-a-dialog-box"></a>Implementación de un cuadro de diálogo

Hay dos maneras de agregar un cuadro de diálogo para el proyecto ATL: usar el Asistente de cuadro de diálogo ATL o agregarlo manualmente.

## <a name="adding-a-dialog-box-with-the-atl-dialog-wizard"></a>Agregar un cuadro de diálogo con el Asistente de cuadro de diálogo ATL

En el [cuadro de diálogo Agregar clase](../ide/add-class-dialog-box.md), seleccione el objeto de cuadro de diálogo ATL para agregar un cuadro de diálogo a un proyecto ATL. Cumplimente el Asistente de cuadro de diálogo ATL según corresponda y haga clic en **finalizar**. El asistente agrega una clase derivada de [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) al proyecto. Abra la vista de recursos desde el **vista** menú, busque el cuadro de diálogo y haga doble clic en él para abrirlo en el editor de recursos.

> [!NOTE]
>  Si se deriva de su cuadro de diálogo `CAxDialogImpl`, puede hospedar tanto ActiveX y controles de Windows. Si no desea la sobrecarga de la compatibilidad con controles ActiveX en la clase de cuadro de diálogo, utilice [CSimpleDialog](../atl/reference/csimpledialog-class.md) o [CDialogImpl](../atl/reference/cdialogimpl-class.md) en su lugar.

Controladores de mensajes y eventos se pueden agregar a la clase de cuadro de diálogo de vista de clases. Para obtener más información, consulte [agregar un controlador de mensajes ATL](../atl/adding-an-atl-message-handler.md).

## <a name="adding-a-dialog-box-manually"></a>Agregar manualmente un cuadro de diálogo

Implementación de un cuadro de diálogo es similar a la implementación de una ventana. Derivar una clase de cualquiera [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md), [CDialogImpl](../atl/reference/cdialogimpl-class.md), o [CSimpleDialog](../atl/reference/csimpledialog-class.md) y declare un [mapa de mensajes](../atl/message-maps-atl.md) para controlar los mensajes. Sin embargo, también debe especificar un identificador de recurso de plantilla de cuadro de diálogo de la clase derivada. La clase debe tener un miembro de datos denominado `IDD` que contenga este valor.

> [!NOTE]
>  Cuando se crea un cuadro de diálogo mediante el Asistente de cuadro de diálogo ATL, el asistente agrega automáticamente el `IDD` miembro como un **enum** tipo.

`CDialogImpl` permite implementar modal o un cuadro de diálogo no modal que hospeda los controles de Windows. `CAxDialogImpl` permite implementar modal o un cuadro de diálogo no modal que hospeda los controles ActiveX y Windows.

Para crear un cuadro de diálogo modal, cree una instancia de su `CDialogImpl`-derivadas (o `CAxDialogImpl`-derivado) de clase y, a continuación, llame a la [DoModal](../atl/reference/cdialogimpl-class.md#domodal) método. Para cerrar el cuadro de diálogo modal, llame a la [EndDialog](../atl/reference/cdialogimpl-class.md#enddialog) método desde un controlador de mensajes. Para crear un cuadro de diálogo no modal, llame a la [crear](../atl/reference/cdialogimpl-class.md#create) método en lugar de `DoModal`. Para destruir un cuadro de diálogo no modal, llame a [DestroyWindow](../atl/reference/cdialogimpl-class.md#destroywindow).

Eventos de recepción se realizan automáticamente en [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md). Implementar controladores de mensajes del cuadro de diálogo como lo haría con los controladores en un `CWindowImpl`-clase derivada. Si hay un valor devuelto de mensaje específicos, como devolver un `LRESULT`. El valor devuelto `LRESULT` ATL asigna los valores para controlar correctamente el administrador del cuadro de diálogo de Windows. Para obtener más información, vea el código fuente de [CDialogImplBaseT:: DialogProc](../atl/reference/cdialogimpl-class.md#dialogproc) en atlwin.h.

## <a name="example"></a>Ejemplo

La clase siguiente implementa un cuadro de diálogo:

[!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/cpp/implementing-a-dialog-box_1.h)]

## <a name="see-also"></a>Vea también

[Clases de ventana](../atl/atl-window-classes.md)

