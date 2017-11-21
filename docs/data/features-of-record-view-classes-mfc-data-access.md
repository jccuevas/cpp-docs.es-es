---
title: "Características de registro Ver clases (acceso a datos MFC) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- record views, classes
- record view classes
ms.assetid: e7b2820f-09c4-483f-83c0-317e8be42bdf
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d1a30742a538d941220cf099c33445089c9a907c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="features-of-record-view-classes--mfc-data-access"></a>Características de las clases de vistas de registros (acceso a datos MFC)
Puede realizar programación de acceso a datos basado en formularios con la clase [CFormView](../mfc/reference/cformview-class.md), pero [CRecordView](../mfc/reference/crecordview-class.md) suele ser una clase se deriva de mejor. Además su `CFormView` características, `CRecordView`:  
  
-   Proporciona el intercambio de datos de cuadros de diálogo (DDX) entre los controles del formulario y el objeto de conjunto de registros asociado.  
  
-   Controla los comandos Mover primero, mover siguiente, mover anterior y Mover último para navegar por los registros en el objeto de conjunto de registros asociado.  
  
-   Actualiza los cambios en el registro actual cuando el usuario se mueve a otro registro.  
  
 Para obtener más información sobre la navegación, consulte [vistas de registros: permitir la navegación en una vista de registros](../data/supporting-navigation-in-a-record-view-mfc-data-access.md).  
  
## <a name="see-also"></a>Vea también  
 [Vistas de registros (acceso a datos MFC)](../data/record-views-mfc-data-access.md)   
 [Lista de controladores ODBC](../data/odbc/odbc-driver-list.md)