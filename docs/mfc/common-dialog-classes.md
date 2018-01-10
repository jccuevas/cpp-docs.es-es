---
title: "Clases de cuadro de diálogo comunes | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fcbed7cec501257f03ab13447d54e081c1d46c76
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="common-dialog-classes"></a>Clases de cuadros de diálogo comunes
Además de la clase [CDialog](../mfc/reference/cdialog-class.md), MFC proporciona varias clases derivadas de `CDialog` que encapsulan cuadros de diálogo de uso frecuente, como se muestra en la tabla siguiente. Los cuadros de diálogo encapsulados se denominan el "cuadros de diálogo comunes" y forman parte de la biblioteca de cuadro de diálogo comunes de Windows (COMMDLG. (DLL). Los recursos de plantilla de cuadro de diálogo y el código para estas clases se proporcionan en las ventanas de cuadros de diálogo comunes que forman parte de las versiones 3.1 y posteriores de Windows.  
  
### <a name="common-dialog-classes"></a>Clases de cuadros de diálogo comunes  
  
|Clase de cuadro de diálogo derivada|Propósito|  
|--------------------------|-------------|  
|[CColorDialog](../mfc/reference/ccolordialog-class.md)|Permite seleccionar colores de usuario.|  
|[CFileDialog](../mfc/reference/cfiledialog-class.md)|Permite al usuario seleccionar un nombre de archivo para abrir o guardar.|  
|[CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)|Permite el usuario inicie una operación de búsqueda o la operación en un archivo de texto de reemplazo.|  
|[CFontDialog](../mfc/reference/cfontdialog-class.md)|Permite al usuario especificar una fuente.|  
|[CPrintDialog](../mfc/reference/cprintdialog-class.md)|Permite el usuario especifique información para un trabajo de impresión.|  
|[CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)|Hoja de propiedades de impresión de Windows 2000.|  
  
 Para obtener más información acerca de las clases de cuadro de diálogo comunes, vea los nombres de clase individuales en el *referencia de MFC*. MFC también proporciona una serie de clases de cuadros de diálogo estándar utilizadas por OLE. Para obtener información sobre estas clases, vea la clase base, [COleDialog](../mfc/reference/coledialog-class.md), en la *referencia de MFC*.  
  
 Otras tres clases en MFC tienen características de tipo cuadro de diálogo. Para obtener información acerca de las clases [CFormView](../mfc/reference/cformview-class.md), [CRecordView](../mfc/reference/crecordview-class.md), y [CDaoRecordView](../mfc/reference/cdaorecordview-class.md), vea las clases en el *referencia de MFC*. Para obtener información acerca de la clase [CDialogBar](../mfc/reference/cdialogbar-class.md), consulte [barras de cuadro de diálogo](../mfc/dialog-bars.md).  
  
## <a name="see-also"></a>Vea también  
 [Cuadros de diálogo](../mfc/dialog-boxes.md)   
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)   
 [Cuadros de diálogo en OLE](../mfc/dialog-boxes-in-ole.md)

