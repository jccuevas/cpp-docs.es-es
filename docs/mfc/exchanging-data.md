---
title: Intercambiar datos
ms.date: 11/04/2016
helpviewer_keywords:
- property sheets [MFC], data exchange
- exchanging data with property sheets [MFC]
- DDX (dialog data exchange) [MFC], property sheets
ms.assetid: 689f02d0-51a9-455b-8ffb-5b44f0aefa28
ms.openlocfilehash: de82a337f19b7b2ac6039fd3f3c16ab67aa1dc99
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405851"
---
# <a name="exchanging-data"></a>Intercambiar datos

Al igual que con la mayoría de los cuadros de diálogo, el intercambio de datos entre la hoja de propiedades y la aplicación es una de las funciones más importantes de la hoja de propiedades. En este artículo se describe cómo realizar esta tarea.

Intercambiar datos con una hoja de propiedades es realmente una cuestión de intercambio de datos con las páginas de propiedades individuales de la hoja de propiedades. El procedimiento para intercambiar datos con una página de propiedades es el mismo que para intercambiar datos con un cuadro de diálogo, ya que un [CPropertyPage](../mfc/reference/cpropertypage-class.md) objeto es simplemente un especializada [CDialog](../mfc/reference/cdialog-class.md) objeto. El procedimiento aprovecha cuadro de diálogo datos (DDX) instalaciones de exchange del marco de trabajo que intercambia datos entre los controles en un cuadro de diálogo cuadro y las variables miembro del objeto de cuadro de diálogo.

La diferencia importante entre el intercambio de datos con una hoja de propiedades y con un cuadro de diálogo normal es que la hoja de propiedades tiene varias páginas, por lo que se deben intercambiar datos con todas las páginas de la hoja de propiedades. Para obtener más información sobre DDX, consulte [intercambio de datos de cuadro de diálogo y validación](../mfc/dialog-data-exchange-and-validation.md).

En el ejemplo siguiente se ilustra el intercambio de datos entre una vista y dos páginas de una hoja de propiedades:

[!code-cpp[NVC_MFCDocView#4](../mfc/codesnippet/cpp/exchanging-data_1.cpp)]

## <a name="see-also"></a>Vea también

[Hojas de propiedades](../mfc/property-sheets-mfc.md)
