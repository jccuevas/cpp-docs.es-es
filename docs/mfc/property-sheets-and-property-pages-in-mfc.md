---
title: Hojas de propiedades y páginas de propiedades en MFC | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property pages [MFC], MFC
- controls [MFC], property sheets
- property sheets, MFC
- tab dialog boxes
ms.assetid: e1bede2b-0285-4b88-a052-0f8a372807a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a54469672c67e43d3692bc47d0b3efa00c18f8f6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348611"
---
# <a name="property-sheets-and-property-pages-in-mfc"></a>Hojas de propiedades y páginas de propiedades en MFC
Una hoja de propiedades, también conocido como un cuadro de diálogo de fichas, es un cuadro de diálogo que contiene páginas de propiedades. Cada página de propiedades se basa en un recurso de plantilla de cuadro de diálogo y contiene controles. Se incluyen en una página con una ficha en la parte superior. La ficha nombres de la página e indica su propósito. Los usuarios, haga clic en una pestaña en la hoja de propiedades para seleccionar un conjunto de controles.  
  
 Use las páginas para agrupar los controles en la hoja de propiedades en conjuntos significativos. La hoja de propiedades independientes normalmente tiene varios controles propios. Éstos se aplican a todas las páginas.  
  
 Hojas de propiedades se basan en la clase [CPropertySheet](../mfc/reference/cpropertysheet-class.md). Páginas de propiedades se basan en la clase [CPropertyPage](../mfc/reference/cpropertypage-class.md).  
  
 Una hoja de propiedades es un tipo especial de cuadro de diálogo que se utiliza normalmente para modificar los atributos de algunos objetos externos, como la selección actual en una vista. La hoja de propiedades tiene tres partes principales: el cuadro de diálogo que contiene páginas de propiedades de uno o más que se muestra uno a uno y una pestaña en la parte superior de cada página que el usuario hace clic para seleccionar esa página. Hojas de propiedades son útiles en situaciones donde haya varios grupos similares de configuración u opciones para cambiar. Una hoja de propiedades agrupa la información de una manera fácil de entender.  
  
> [!NOTE]
>  Cuando se está intentando mostrar una hoja de propiedades mediante el uso de `CPropertySheet::DoModal`, el sistema podría generar una excepción de primera oportunidad. Esta excepción se produce porque el sistema está intentando cambiar la [estilos de ventana](../mfc/reference/styles-used-by-mfc.md#window-styles) del objeto antes de que se ha creado el objeto. Para obtener más información sobre esta excepción y también cómo evitar esta situación o controlarla, consulte [CPropertySheet:: DoModal](../mfc/reference/cpropertysheet-class.md#domodal).  
  
## <a name="see-also"></a>Vea también  
 [Hojas de propiedades](../mfc/property-sheets-mfc.md)

