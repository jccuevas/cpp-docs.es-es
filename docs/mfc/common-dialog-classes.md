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
ms.openlocfilehash: d11d0978763d9599b0471a8e994f15a267f7cb8f
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685559"
---
# <a name="common-dialog-classes"></a>Clases de cuadros de diálogo comunes

Además de la clase [CDialog](../mfc/reference/cdialog-class.md), MFC proporciona varias clases derivadas de `CDialog` que encapsulan los cuadros de diálogo utilizados con frecuencia, como se muestra en la tabla siguiente. Los cuadros de diálogo encapsulados se denominan "cuadros de diálogo comunes" y forman parte de la biblioteca de cuadros de diálogo comunes de Windows (COMMDLG). DLL). Los recursos de plantilla de cuadro de diálogo y el código para estas clases se proporcionan en los cuadros de diálogo comunes de Windows que forman parte de las versiones de Windows 3,1 y posteriores.

### <a name="common-dialog-classes"></a>Clases de cuadros de diálogo comunes

|Clase de cuadro de diálogo derivada|Finalidad|
|--------------------------|-------------|
|[CColorDialog](../mfc/reference/ccolordialog-class.md)|Permite que el usuario seleccione los colores.|
|[CFileDialog](../mfc/reference/cfiledialog-class.md)|Permite al usuario seleccionar un nombre de archivo para abrirlo o guardarlo.|
|[CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)|Permite al usuario iniciar una operación de búsqueda o reemplazo en un archivo de texto.|
|[CFontDialog](../mfc/reference/cfontdialog-class.md)|Permite al usuario especificar una fuente.|
|[CPrintDialog](../mfc/reference/cprintdialog-class.md)|Permite al usuario especificar la información de un trabajo de impresión.|
|[CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)|Hoja de propiedades de impresión de Windows.|

Para obtener más información sobre las clases de cuadro de diálogo comunes, vea los nombres de clase individuales en la *referencia de MFC*. MFC también proporciona una serie de clases de cuadro de diálogo estándar que se usan para OLE. Para obtener información sobre estas clases, vea la clase base, [COleDialog](../mfc/reference/coledialog-class.md), en la *referencia de MFC*.

Otras tres clases de MFC tienen características similares a los cuadros de diálogo. Para obtener información sobre las clases [CFormView](../mfc/reference/cformview-class.md), [CRecordView](../mfc/reference/crecordview-class.md)y [CDaoRecordView](../mfc/reference/cdaorecordview-class.md), vea las clases de la *referencia de MFC*. Para obtener información sobre la clase [CDialogBar](../mfc/reference/cdialogbar-class.md), vea [barras de cuadro de diálogo](../mfc/dialog-bars.md).

## <a name="see-also"></a>Vea también

[Cuadros de diálogo](../mfc/dialog-boxes.md)<br/>
[Trabajar con cuadros de diálogo en MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Cuadros de diálogo en OLE](../mfc/dialog-boxes-in-ole.md)
