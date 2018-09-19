---
title: Intercambiar datos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property sheets [MFC], data exchange
- exchanging data with property sheets [MFC]
- DDX (dialog data exchange) [MFC], property sheets
ms.assetid: 689f02d0-51a9-455b-8ffb-5b44f0aefa28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e503bd9268423fbe63ec76de4bcb5443a7d52696
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345825"
---
# <a name="exchanging-data"></a>Intercambiar datos
Al igual que con la mayoría de los cuadros de diálogo, el intercambio de datos entre la hoja de propiedades y la aplicación es una de las funciones más importantes de la hoja de propiedades. En este artículo se describe cómo realizar esta tarea.  
  
 Intercambiar datos con una hoja de propiedades es realmente una cuestión de intercambiar datos con las páginas de propiedades individuales de la hoja de propiedades. El procedimiento para intercambiar datos con una página de propiedades es el mismo que para intercambiar datos con un cuadro de diálogo, ya que un [CPropertyPage](../mfc/reference/cpropertypage-class.md) objeto es simplemente un especializado [CDialog](../mfc/reference/cdialog-class.md) objeto. El procedimiento aprovecha la utilidad del intercambio (DDX) datos del marco de trabajo cuadro de diálogo que intercambia datos entre los controles en un cuadro de diálogo cuadro y las variables miembro del objeto de cuadro de diálogo.  
  
 La diferencia importante entre el intercambio de datos con una hoja de propiedades y con un cuadro de diálogo normal es que la hoja de propiedades tiene varias páginas, por lo que se deben intercambiar datos con todas las páginas de la hoja de propiedades. Para obtener más información sobre DDX, consulte [intercambio de datos de cuadros de diálogo y validación](../mfc/dialog-data-exchange-and-validation.md).  
  
 En el ejemplo siguiente se muestra el intercambio de datos entre una vista y dos páginas de una hoja de propiedades:  
  
 [!code-cpp[NVC_MFCDocView#4](../mfc/codesnippet/cpp/exchanging-data_1.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Hojas de propiedades](../mfc/property-sheets-mfc.md)

