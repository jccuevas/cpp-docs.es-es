---
title: Hojas de propiedades y páginas de propiedades en MFC
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC
- controls [MFC], property sheets
- property sheets, MFC
- tab dialog boxes
ms.assetid: e1bede2b-0285-4b88-a052-0f8a372807a2
ms.openlocfilehash: 10fb34c79745e672d30dd2d3c3b97d457583f795
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371170"
---
# <a name="property-sheets-and-property-pages-in-mfc"></a>Hojas de propiedades y páginas de propiedades en MFC

Una hoja de propiedades, también conocida como cuadro de diálogo de ficha, es un cuadro de diálogo que contiene páginas de propiedades. Cada página de propiedades se basa en un recurso de plantilla de cuadro de diálogo y contiene controles. Se adjunta en una página con una pestaña en la parte superior. La pestaña nombra la página e indica su propósito. Los usuarios hacen clic en una pestaña de la hoja de propiedades para seleccionar un conjunto de controles.

Utilice páginas para agrupar los controles de la hoja de propiedades en conjuntos significativos. La hoja de propiedades contenida normalmente tiene varios controles propios. Estos se aplican a todas las páginas.

Las hojas de propiedades se basan en la clase [CPropertySheet](../mfc/reference/cpropertysheet-class.md). Las páginas de propiedades se basan en la clase [CPropertyPage](../mfc/reference/cpropertypage-class.md).

Una hoja de propiedades es un tipo especial de cuadro de diálogo que se utiliza generalmente para modificar los atributos de algún objeto externo, como la selección actual en una vista. La hoja de propiedades tiene tres partes principales: el cuadro de diálogo contenedor, una o varias páginas de propiedades que se muestran una a la vez y una pestaña en la parte superior de cada página en la que el usuario hace clic para seleccionar esa página. Las hojas de propiedades son útiles para situaciones en las que tiene varios grupos similares de configuraciones u opciones que cambiar. Una hoja de propiedades agrupa la información de una manera fácil de entender.

> [!NOTE]
> Cuando se intenta mostrar una hoja `CPropertySheet::DoModal`de propiedades mediante , el sistema puede generar una excepción de primera oportunidad. Esta excepción se produce porque el sistema está intentando cambiar los [estilos](../mfc/reference/styles-used-by-mfc.md#window-styles) de ventana del objeto antes de que se haya creado el objeto. Para obtener más información acerca de esta excepción y también cómo evitarla o controlarla, vea [CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal).

## <a name="see-also"></a>Consulte también

[Hojas de propiedades](../mfc/property-sheets-mfc.md)
