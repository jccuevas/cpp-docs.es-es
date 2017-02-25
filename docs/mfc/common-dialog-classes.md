---
title: "Clases de cuadros de di&#225;logo comunes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cuadros de diálogo comunes [C++]"
  - "cuadros de diálogo comunes [C++], clases de cuadros de diálogo comunes"
  - "clases de cuadros de diálogo comunes [C++]"
  - "cuadros de diálogo [C++], cuadros de diálogo comunes de Windows"
  - "clases de cuadro de diálogo [C++]"
  - "clases de cuadro de diálogo [C++], común"
  - "cuadros de diálogo de MFC, cuadros de diálogo comunes de Windows"
  - "cuadros de diálogo comunes de Windows [C++]"
ms.assetid: 5c4f6443-896c-4b05-a7df-8169fdadc71d
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Clases de cuadros de di&#225;logo comunes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Además de la clase [CDialog](../mfc/reference/cdialog-class.md), MFC proporciona que varias clases derivadas de `CDialog` que encapsulan los cuadros de diálogo de uso común, como se muestra en la tabla siguiente.  Los cuadros de diálogo encapsulados se denominan “cuadros de diálogo comunes” y son parte de la biblioteca común del diálogo de Windows \(COMMDLG.DLL\).  Proporcionan los recursos y el código de la diálogo\- plantilla para estas clases en los cuadros de diálogo comunes de Windows que forman parte de las versiones de Windows 3,1 y versiones posteriores.  
  
### Clases comunes de diálogo  
  
|Clase derivada de diálogo|Objetivo|  
|-------------------------------|--------------|  
|[CColorDialog](../mfc/reference/ccolordialog-class.md)|Permite al usuario seleccionar colores.|  
|[CFileDialog](../mfc/reference/cfiledialog-class.md)|Permite al usuario seleccionar un nombre de archivo para abrir o guardar.|  
|[CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)|Permite al usuario iniciar una búsqueda o de reemplazo en un archivo de texto.|  
|[CFontDialog](../mfc/reference/cfontdialog-class.md)|Permite al usuario especificar una fuente.|  
|[CPrintDialog](../mfc/reference/cprintdialog-class.md)|Permite al usuario especificar la información para un trabajo de impresión.|  
|[CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)|Hoja de propiedades de impresión de Windows 2000.|  
  
 Para obtener más información sobre las clases comunes de cuadro de diálogo, vea los nombres de clase individuales en *la referencia de MFC*.  MFC también proporciona varias clases estándar de diálogo utilizadas para OLE.  Para obtener información sobre estas clases, vea la clase base, [COleDialog](../mfc/reference/coledialog-class.md), en *la referencia de MFC*.  
  
 Otras tres clases de MFC tienen diálogo\- como características.  Para obtener información sobre las clases [CFormView](../mfc/reference/cformview-class.md), [CRecordView](../mfc/reference/crecordview-class.md), y [CDaoRecordView](../mfc/reference/cdaorecordview-class.md), vea las clases en *la referencia de MFC*.  Para obtener información sobre la clase [CDialogBar](../mfc/reference/cdialogbar-class.md), vea [Barras de cuadro de diálogo](../mfc/dialog-bars.md).  
  
## Vea también  
 [Cuadros de diálogo](../mfc/dialog-boxes.md)   
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)   
 [Cuadros de diálogo en OLE](../mfc/dialog-boxes-in-ole.md)