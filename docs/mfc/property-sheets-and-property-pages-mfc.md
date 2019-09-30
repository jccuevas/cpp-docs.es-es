---
title: Hojas de propiedades y páginas de propiedades (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], tabs
- property pages [MFC], property sheets
- CPropertyPage class [MFC], property sheets and pages
- CPropertySheet class [MFC], property sheets and pages
- property sheets, propert pages
ms.assetid: de8fea12-6c35-4cef-8625-b8073a379446
ms.openlocfilehash: 5d4fd1c957b7f4d0d6ad10379a448309743aa11a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685082"
---
# <a name="property-sheets-and-property-pages-mfc"></a>Hojas de propiedades y páginas de propiedades (MFC)

Un [cuadro de diálogo](../mfc/dialog-boxes.md) MFC puede tomar el aspecto de un "cuadro de diálogo de pestaña" mediante la incorporación de hojas de propiedades y páginas de propiedades. Denominada "hoja de propiedades" en MFC, este tipo de cuadro de diálogo, similar a muchos cuadros de diálogo de Microsoft Word, Excel y C++visual, parece contener una pila de hojas con pestañas, como una pila de carpetas de archivos que se ve de delante a atrás, o un grupo de ventanas en cascada. Los controles de la pestaña frontal están visibles; solo la pestaña con etiqueta está visible en las pestañas posteriores. Las hojas de propiedades son especialmente útiles para administrar un gran número de propiedades o valores de configuración que se encuentran bastante ordenados en varios grupos. Normalmente, una hoja de propiedades puede simplificar una interfaz de usuario mediante la sustitución de varios cuadros de diálogo independientes.

A partir de la versión 4,0 de MFC, las hojas de propiedades y las páginas de propiedades se implementan utilizando los controles comunes que se incluyen con Windows 95 y Windows NT versión 3,51 y versiones posteriores.

Las hojas de propiedades se implementan con las clases [CPropertySheet](../mfc/reference/cpropertysheet-class.md) y [CPropertyPage](../mfc/reference/cpropertypage-class.md) (descritas en la *referencia de MFC*). `CPropertySheet` define el cuadro de diálogo general, que puede contener varias "páginas" basadas en `CPropertyPage`.

Para obtener información sobre cómo crear y trabajar con hojas de propiedades, vea el tema de las [hojas de propiedades](../mfc/property-sheets-mfc.md).

## <a name="see-also"></a>Vea también

[Cuadros de diálogo](../mfc/dialog-boxes.md)<br/>
[Trabajar con cuadros de diálogo en MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Hojas de propiedades y páginas de propiedades en MFC](../mfc/property-sheets-and-property-pages-in-mfc.md)<br/>
[Intercambio de datos](../mfc/exchanging-data.md)<br/>
[Creación de una hoja de propiedades no modal](../mfc/creating-a-modeless-property-sheet.md)<br/>
[Control del botón Aplicar](../mfc/handling-the-apply-button.md)
