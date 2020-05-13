---
title: Mostrar y manipular datos en un formulario
ms.date: 11/04/2016
helpviewer_keywords:
- forms [C++], displaying data
- displaying data [C++], forms
- ODBC [C++], forms
- record views [C++], displaying data
- data [MFC]
- data [MFC], displaying in a form
ms.assetid: c56185c4-12cb-40b1-b499-02b29ea83e3a
ms.openlocfilehash: 6b663fabd0c87d9a2773e6f5a2796bcc8f57ce29
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213257"
---
# <a name="displaying-and-manipulating-data-in-a-form"></a>Mostrar y manipular datos en un formulario

Muchas aplicaciones de acceso a datos seleccionan datos y lo muestran en los campos de un formulario. La clase de base de datos [CRecordView](../../mfc/reference/crecordview-class.md) le proporciona un objeto [CFormView](../../mfc/reference/cformview-class.md) directamente conectado a un objeto de conjunto de registros. La vista de registros usa el [intercambio de datos de cuadros de diálogo (DDX)](../../mfc/dialog-data-exchange-and-validation.md) para trasladar los valores de los campos del registro actual del conjunto de registros a los controles del formulario y para devolver la información actualizada al conjunto de registros. El conjunto de registros, a su vez, usa el intercambio de campos de registros (RFX) para trasladar los datos entre sus miembros de datos de campo y las columnas correspondientes de una tabla en el origen de datos.

Puede usar el Asistente para aplicaciones MFC o **Agregar clase** (como se describe en [Agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) para crear la clase de vista y su clase de conjunto de registros asociada conjuntamente.

La vista de registros y su conjunto de registros se destruyen cuando se cierra el documento. Para obtener más información acerca de las vistas de registros, consulte [vistas de registros](../../data/record-views-mfc-data-access.md). Para obtener más información sobre RFX, consulte [intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md).

## <a name="see-also"></a>Consulte también

[ODBC y MFC](../../data/odbc/odbc-and-mfc.md)
