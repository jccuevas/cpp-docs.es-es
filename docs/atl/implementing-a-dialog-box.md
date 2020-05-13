---
title: Implementación de un cuadro de diálogo
ms.date: 11/04/2016
helpviewer_keywords:
- CSimpleDialog class, implementing dialog boxes in ATL
- dialog boxes, ATL
- CAxDialogImpl class, implementing dialog boxes in ATL
- ATL, dialog boxes
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
ms.openlocfilehash: 435926b0a0affde03580ceb2b479cb08a17d0454
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319474"
---
# <a name="implementing-a-dialog-box"></a>Implementación de un cuadro de diálogo

Hay dos maneras de agregar un cuadro de diálogo al proyecto ATL: utilice el Asistente para cuadros de diálogo ATL o agréguelo manualmente.

## <a name="adding-a-dialog-box-with-the-atl-dialog-wizard"></a>Agregar un cuadro de diálogo con el Asistente para cuadros de diálogo ATL

En el cuadro de [diálogo Agregar clase](../ide/add-class-dialog-box.md), seleccione el objeto Diálogo ATL para agregar un cuadro de diálogo al proyecto ATL. Rellene el Asistente para cuadros de diálogo ATL según corresponda y haga clic en **Finalizar**. El asistente agrega una clase derivada de [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) al proyecto. Abra **vista** de recursos en el menú **Ver,** busque el cuadro de diálogo y haga doble clic en él para abrirlo en el editor de recursos.

> [!NOTE]
> Si el cuadro de `CAxDialogImpl`diálogo se deriva de , puede hospedar controles ActiveX y Windows. Si no desea que la sobrecarga de compatibilidad con controles ActiveX en la clase de cuadro de diálogo, utilice [CSimpleDialog](../atl/reference/csimpledialog-class.md) o [CDialogImpl](../atl/reference/cdialogimpl-class.md) en su lugar.

Controladores de mensajes y eventos se pueden agregar a la clase de cuadro de diálogo desde la vista de clases. Para obtener más información, vea Agregar un controlador de mensajes [ATL](../atl/adding-an-atl-message-handler.md).

## <a name="adding-a-dialog-box-manually"></a>Adición manual de un cuadro de diálogo

Implementar un cuadro de diálogo es similar a implementar una ventana. Derive una clase de [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md), [CDialogImpl](../atl/reference/cdialogimpl-class.md)o [CSimpleDialog](../atl/reference/csimpledialog-class.md) y declare un mapa de [mensajes](../atl/message-maps-atl.md) para controlar los mensajes. Sin embargo, también debe especificar un identificador de recurso de plantilla de cuadro de diálogo en la clase derivada. La clase debe tener `IDD` un miembro de datos llamado para contener este valor.

> [!NOTE]
> Al crear un cuadro de diálogo mediante el Asistente para `IDD` cuadros de diálogo ATL, el asistente agrega automáticamente el miembro como un tipo **de enumeración.**

`CDialogImpl`le permite implementar un cuadro de diálogo modal o no modal que hospeda controles de Windows. `CAxDialogImpl`permite implementar un cuadro de diálogo modal o no modal que hospeda controles ActiveX y Windows.

Para crear un cuadro de diálogo `CDialogImpl`modal, cree `CAxDialogImpl`una instancia de la clase -derived (o -derived) y, a continuación, llame a la [DoModal](../atl/reference/cdialogimpl-class.md#domodal) método. Para cerrar un cuadro de diálogo modal, llame a la [EndDialog](../atl/reference/cdialogimpl-class.md#enddialog) método desde un controlador de mensajes. Para crear un cuadro de diálogo no especificador, llame al método [Create](../atl/reference/cdialogimpl-class.md#create) en lugar de `DoModal`. Para destruir un cuadro de diálogo no qued, llame a [DestroyWindow](../atl/reference/cdialogimpl-class.md#destroywindow).

Los eventos de hundimiento se realizan automáticamente en [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md). Implemente los controladores de mensajes del cuadro de `CWindowImpl`diálogo como lo haría con los controladores de una clase derivada. Si hay un valor devuelto específico del `LRESULT`mensaje, devuélvalo como un archivo . ATL `LRESULT` asigna los valores devueltos para que el administrador de cuadros de diálogo de Windows los controle correctamente. Para obtener más información, vea el código fuente de [CDialogImplBaseT::DialogProc](../atl/reference/cdialogimpl-class.md#dialogproc) en atlwin.h.

## <a name="example"></a>Ejemplo

La siguiente clase implementa un cuadro de diálogo:

[!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/cpp/implementing-a-dialog-box_1.h)]

## <a name="see-also"></a>Consulte también

[Clases de ventanas](../atl/atl-window-classes.md)
