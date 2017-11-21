---
title: Intercambio de datos para vistas de registros (acceso a datos MFC) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- RFX (record field exchange), data exchange mechanism
- RFX (record field exchange), record views
- record views, data exchange
- DDX (dialog data exchange), record views
- RFX (record field exchange)
ms.assetid: abc52ca7-6997-47a7-98f3-f347f52b1f72
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 564ff17037bfa86000329ed66b67a9b9ba76c879
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="data-exchange-for-record-views---mfc-data-access"></a>Intercambio de datos para vistas de registros (acceso a datos MFC)
Cuando usas [Agregar clase](../mfc/reference/adding-an-mfc-odbc-consumer.md) para asignar los controles de recurso de plantilla de cuadro de diálogo de una vista de registros a los campos de un conjunto de registros, el marco de trabajo administra el intercambio de datos en ambas direcciones: desde el conjunto de registros a los controles y desde los controles al conjunto de registros. Si utiliza el mecanismo DDX, no tiene que escribir por su cuenta el código para transferir los datos en ambos sentidos.  
  
 DDX para vistas de registros funciona junto con [RFX](../data/odbc/record-field-exchange-rfx.md) para conjuntos de registros de clase `CRecordset` (ODBC).  RFX mueve datos entre el registro actual del origen de datos y los miembros de datos de campo de un objeto de conjunto de registros. DDX mueve los datos de los miembros de datos de campo a los controles del formulario. Esta combinación rellena los controles del formulario al principio y a medida que el usuario se desplaza por los registros. Pueden también devolver los datos actualizados al conjunto de registros y, a continuación, moverlos al origen de datos.  
  
 En la siguiente ilustración muestra la relación entre DDX y RFX para vistas de registros.  
  
 ![Cuadro de diálogo &#45; intercambio de datos y registro &#45; intercambio de campos de](../data/media/vc37xt1.gif "vc37xt1")  
Intercambio de datos de cuadro de diálogo e intercambio de campos de registros  
  
 Para obtener más información sobre DDX, consulte [intercambio de datos de cuadros de diálogo y validación](../mfc/dialog-data-exchange-and-validation.md). Para obtener más información sobre RFX, consulte [intercambio de campos de registros (RFX)](../data/odbc/record-field-exchange-rfx.md).  
  
## <a name="see-also"></a>Vea también  
 [Vistas de registros (acceso a datos MFC)](../data/record-views-mfc-data-access.md)   
 [Lista de controladores ODBC](../data/odbc/odbc-driver-list.md)