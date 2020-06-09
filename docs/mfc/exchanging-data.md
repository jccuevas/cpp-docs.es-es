---
title: Intercambiar datos
ms.date: 11/04/2016
helpviewer_keywords:
- property sheets [MFC], data exchange
- exchanging data with property sheets [MFC]
- DDX (dialog data exchange) [MFC], property sheets
ms.assetid: 689f02d0-51a9-455b-8ffb-5b44f0aefa28
ms.openlocfilehash: 5be82567e02fd5e935d42f9eff5bdee20fa0d5a8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622703"
---
# <a name="exchanging-data"></a>Intercambiar datos

Al igual que en la mayoría de los cuadros de diálogo, el intercambio de datos entre la hoja de propiedades y la aplicación es una de las funciones más importantes de la hoja de propiedades. En este artículo se describe cómo realizar esta tarea.

El intercambio de datos con una hoja de propiedades es realmente una cuestión de intercambiar datos con las páginas de propiedades individuales de la hoja de propiedades. El procedimiento para intercambiar datos con una página de propiedades es el mismo que el de intercambiar datos con un cuadro de diálogo, ya que un objeto [CPropertyPage](reference/cpropertypage-class.md) es simplemente un objeto [CDialog](reference/cdialog-class.md) especializado. El procedimiento aprovecha la utilidad de intercambio de datos de cuadros de diálogo (DDX) del marco, que intercambia datos entre los controles de un cuadro de diálogo y las variables de miembro del objeto de cuadro de diálogo.

La diferencia importante entre intercambiar datos con una hoja de propiedades y con un cuadro de diálogo normal es que la hoja de propiedades tiene varias páginas, por lo que debe intercambiar datos con todas las páginas de la hoja de propiedades. Para obtener más información sobre DDX, consulte [intercambio y validación de datos de cuadros de diálogo](dialog-data-exchange-and-validation.md).

En el ejemplo siguiente se muestra cómo intercambiar datos entre una vista y dos páginas de una hoja de propiedades:

[!code-cpp[NVC_MFCDocView#4](codesnippet/cpp/exchanging-data_1.cpp)]

## <a name="see-also"></a>Consulte también

[Hojas de propiedades](property-sheets-mfc.md)
