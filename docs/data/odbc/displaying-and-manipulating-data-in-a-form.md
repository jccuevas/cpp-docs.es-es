---
title: Mostrar y manipular datos en un formulario | Microsoft Docs
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
ms.openlocfilehash: 6d09245bdf05f770e6b0e3161cf71902944b608c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103651"
---
# <a name="displaying-and-manipulating-data-in-a-form"></a>Mostrar y manipular datos en un formulario

Muchas aplicaciones de acceso a datos seleccione datos y mostrarlos en los campos de un formulario. La clase base de datos [CRecordView](../../mfc/reference/crecordview-class.md) le ofrece un [CFormView](../../mfc/reference/cformview-class.md) objeto conectado directamente a un objeto de conjunto de registros. La vista de registros usa [intercambio de datos de cuadro de diálogo (DDX)](../../mfc/dialog-data-exchange-and-validation.md) para mover los valores de los campos del registro actual del conjunto de registros a los controles del formulario y devolver la información actualizada para el conjunto de registros. El conjunto de registros, a su vez, usa intercambio de campos de registros (RFX) para mover datos entre sus miembros de datos de campo y las columnas correspondientes de una tabla en el origen de datos.  
  
Puede usar el Asistente para aplicaciones MFC o **Agregar clase** (como se describe en [agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) para crear la clase de vista y su clase de conjunto de registros asociado conjuntamente.  
  
La vista de registros y su conjunto de registros se destruyen al cerrar el documento. Para obtener más información acerca de las vistas de registros, vea [vistas de registros](../../data/record-views-mfc-data-access.md). Para obtener más información sobre RFX, consulte [intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
## <a name="see-also"></a>Vea también  

[ODBC y MFC](../../data/odbc/odbc-and-mfc.md)