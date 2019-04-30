---
title: Hojas de propiedades y páginas de propiedades en MFC
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC
- controls [MFC], property sheets
- property sheets, MFC
- tab dialog boxes
ms.assetid: e1bede2b-0285-4b88-a052-0f8a372807a2
ms.openlocfilehash: fa8ee3518ad2b32e0eace77f0961eb86ccde1822
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391379"
---
# <a name="property-sheets-and-property-pages-in-mfc"></a>Hojas de propiedades y páginas de propiedades en MFC

Una hoja de propiedades, también conocido como un cuadro de diálogo de pestaña, es un cuadro de diálogo que contiene las páginas de propiedades. Cada página de propiedades se basa en un recurso de plantilla de cuadro de diálogo y contiene controles. Que se incluye en una página con una pestaña en la parte superior. La pestaña los nombres de la página e indica su propósito. Los usuarios, haga clic en una pestaña en la hoja de propiedades para seleccionar un conjunto de controles.

Use las páginas para agrupar los controles en la hoja de propiedades en conjuntos significativos. Normalmente, la hoja de propiedades independiente tiene varios controles propios. Estas se aplican a todas las páginas.

Hojas de propiedades se basan en la clase [CPropertySheet](../mfc/reference/cpropertysheet-class.md). Páginas de propiedades se basan en la clase [CPropertyPage](../mfc/reference/cpropertypage-class.md).

Una hoja de propiedades es un tipo especial de cuadro de diálogo que se usa generalmente para modificar los atributos de algunos objetos externos, como la selección actual en una vista. La hoja de propiedades tiene tres partes principales: el cuadro de diálogo que contiene páginas de propiedades de uno o más que uno se muestra a la vez y una pestaña en la parte superior de cada página que el usuario hace clic para seleccionar esa página. Hojas de propiedades son útiles para situaciones donde tiene varios grupos similar de configuración u opciones para cambiar. Una hoja de propiedades agrupa la información de una manera fácil de entender.

> [!NOTE]
>  Cuando se está intentando mostrar una hoja de propiedades mediante el uso de `CPropertySheet::DoModal`, el sistema podría generar una excepción de primera oportunidad. Esta excepción se produce porque el sistema está intentando cambiar la [estilos de ventana](../mfc/reference/styles-used-by-mfc.md#window-styles) del objeto antes de que se ha creado el objeto. Para obtener más información acerca de esta excepción y también cómo evitarla o controlarlo, consulte [CPropertySheet:: DoModal](../mfc/reference/cpropertysheet-class.md#domodal).

## <a name="see-also"></a>Vea también

[Hojas de propiedades](../mfc/property-sheets-mfc.md)
