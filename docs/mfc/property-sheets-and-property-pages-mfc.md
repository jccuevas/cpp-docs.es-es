---
title: Hojas de propiedades y páginas de propiedades (MFC) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], tabs
- property pages [MFC], property sheets
- CPropertyPage class [MFC], property sheets and pages
- CPropertySheet class [MFC], property sheets and pages
- property sheets, propert pages
ms.assetid: de8fea12-6c35-4cef-8625-b8073a379446
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 882b2d93ba7938017f64b1ad8fb8e680e0af42db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="property-sheets-and-property-pages-mfc"></a>Hojas de propiedades y páginas de propiedades (MFC)
MFC [cuadro de diálogo](../mfc/dialog-boxes.md) puede tardar en una búsqueda de "cuadro de diálogo de pestaña" mediante la incorporación de hojas de propiedades y páginas de propiedades. Llama a una "hoja de propiedades" en MFC, este tipo de cuadro de diálogo, parecido a muchos cuadros de diálogo en Microsoft Word, Excel y Visual C++, parece contener una pila de hojas con pestañas, como una pila de carpetas vistas de delante hacia atrás, o un grupo de ventanas en cascada. Controles de la primera ficha están visibles; solo la etiqueta de la ficha está visible en las pestañas posteriores. Hojas de propiedades son especialmente útiles para administrar un gran número de propiedades o configuraciones que se pueden dividir en varios grupos. Normalmente, una hoja de propiedades puede simplificar una interfaz de usuario mediante la sustitución de varios cuadros de diálogo independiente.  
  
 A partir de la versión 4.0 de MFC, las hojas de propiedades y páginas de propiedades se implementan utilizando los controles comunes que vienen con Windows 95 y Windows NT versión 3.51 y posterior.  
  
 Hojas de propiedades se implementan con las clases de [CPropertySheet](../mfc/reference/cpropertysheet-class.md) y [CPropertyPage](../mfc/reference/cpropertypage-class.md) (se describe en el *referencia de MFC*). `CPropertySheet` define el cuadro de diálogo general, que puede contener varias "páginas" basadas en `CPropertyPage`.  
  
 Para obtener información sobre cómo crear y trabajar con hojas de propiedades, vea el tema [hojas de propiedades](../mfc/property-sheets-mfc.md).  
  
## <a name="see-also"></a>Vea también  
 [Cuadros de diálogo](../mfc/dialog-boxes.md)   
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)   
 [Hojas de propiedades y páginas de propiedades en MFC](../mfc/property-sheets-and-property-pages-in-mfc.md)   
 [Intercambio de datos](../mfc/exchanging-data.md)   
 [Crear una hoja de propiedades no modales](../mfc/creating-a-modeless-property-sheet.md)   
 [Control del botón Aplicar](../mfc/handling-the-apply-button.md)

