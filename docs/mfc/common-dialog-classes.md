---
title: Clases de cuadros de diálogo comunes
ms.date: 11/04/2016
helpviewer_keywords:
- dialog classes [MFC]
- dialog boxes [MFC], Windows common dialogs
- common dialog boxes [MFC], common dialog classes
- common dialog classes [MFC]
- MFC dialog boxes [MFC], Windows common dialogs
- Windows common dialogs [MFC]
- dialog classes [MFC], common
- common dialog boxes [MFC]
ms.assetid: 5c4f6443-896c-4b05-a7df-8169fdadc71d
ms.openlocfilehash: 5efd885421d8c73c191e2a5603f37d1df85a5168
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303079"
---
# <a name="common-dialog-classes"></a>Clases de cuadros de diálogo comunes

Además de la clase [CDialog](../mfc/reference/cdialog-class.md), MFC proporciona varias clases derivadas de `CDialog` que encapsulan los cuadros de diálogo frecuente, como se muestra en la tabla siguiente. Encapsulada los cuadros de diálogo se denominan el "cuadros de diálogo comunes" y forman parte de la biblioteca de cuadro de diálogo comunes de Windows (COMMDLG. (DLL). Los recursos de plantilla de cuadro de diálogo y el código para estas clases se muestran en el Windows cuadros de diálogo comunes que forman parte de las versiones 3.1 y posteriores de Windows.

### <a name="common-dialog-classes"></a>Clases de cuadros de diálogo comunes

|Clase de cuadro de diálogo derivada|Propósito|
|--------------------------|-------------|
|[CColorDialog](../mfc/reference/ccolordialog-class.md)|Permite el usuario seleccionar colores.|
|[CFileDialog](../mfc/reference/cfiledialog-class.md)|Permite el usuario seleccione un nombre de archivo para abrir o guardar.|
|[CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)|Permite el usuario inicie una búsqueda o la operación en un archivo de texto de reemplazo.|
|[CFontDialog](../mfc/reference/cfontdialog-class.md)|Permite al usuario especificar una fuente.|
|[CPrintDialog](../mfc/reference/cprintdialog-class.md)|Permite al usuario especificar información para un trabajo de impresión.|
|[CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)|Hoja de propiedades de impresión de Windows.|

Para obtener más información acerca de las clases de cuadro de diálogo comunes, vea los nombres de clase individuales en el *referencia de MFC*. MFC también proporciona una serie de clases de cuadro de diálogo estándar utilizadas por OLE. Para obtener información sobre estas clases, vea la clase base, [COleDialog](../mfc/reference/coledialog-class.md), en el *referencia de MFC*.

Otras tres clases de MFC tienen características de tipo cuadro de diálogo. Para obtener información acerca de las clases [CFormView](../mfc/reference/cformview-class.md), [CRecordView](../mfc/reference/crecordview-class.md), y [CDaoRecordView](../mfc/reference/cdaorecordview-class.md), vea las clases en el *referencia de MFC*. Para obtener información acerca de la clase [CDialogBar](../mfc/reference/cdialogbar-class.md), consulte [barras de cuadro de diálogo](../mfc/dialog-bars.md).

## <a name="see-also"></a>Vea también

[Cuadros de diálogo](../mfc/dialog-boxes.md)<br/>
[Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Cuadros de diálogo en OLE](../mfc/dialog-boxes-in-ole.md)
