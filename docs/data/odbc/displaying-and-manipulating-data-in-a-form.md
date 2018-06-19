---
title: Mostrar y manipular datos en un formulario | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- forms [C++], displaying data
- displaying data [C++], forms
- ODBC [C++], forms
- record views [C++], displaying data
- data [MFC]
- data [MFC], displaying in a form
ms.assetid: c56185c4-12cb-40b1-b499-02b29ea83e3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3b86c58c8e5afb53cb02174beb3553378dd0efc8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089371"
---
# <a name="displaying-and-manipulating-data-in-a-form"></a>Mostrar y manipular datos en un formulario
Muchas aplicaciones de acceso a datos seleccione datos y mostrarlos en campos de un formulario. La clase de base de datos [CRecordView](../../mfc/reference/crecordview-class.md) le ofrece un [CFormView](../../mfc/reference/cformview-class.md) objeto conectado directamente a un objeto de conjunto de registros. La vista de registros utiliza [intercambio de datos de cuadros de diálogo (DDX)](../../mfc/dialog-data-exchange-and-validation.md) para mover los valores de los campos del registro actual del conjunto de registros a los controles en el formulario y para mover información actualizada de vuelta al conjunto de registros. El conjunto de registros, a su vez, utiliza el intercambio de campos de registros (RFX) para mover datos entre sus miembros de datos de campo y las columnas correspondientes de una tabla en el origen de datos.  
  
 Puede usar el Asistente para aplicaciones MFC o **Agregar clase** (como se describe en [agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) para crear la clase de vista y su clase de conjunto de registros asociada conjuntamente.  
  
 La vista de registros y su conjunto de registros se destruyen cuando se cierra el documento. Para obtener más información sobre vistas de registros, vea [vistas de registros](../../data/record-views-mfc-data-access.md). Para obtener más información sobre RFX, consulte [intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
## <a name="see-also"></a>Vea también  
 [ODBC y MFC](../../data/odbc/odbc-and-mfc.md)