---
title: Intercambio de datos para vistas de registros (acceso a datos MFC)
ms.date: 11/19/2018
helpviewer_keywords:
- RFX (record field exchange), data exchange mechanism
- RFX (record field exchange), record views
- record views, data exchange
- DDX (dialog data exchange), record views
- RFX (record field exchange)
ms.assetid: abc52ca7-6997-47a7-98f3-f347f52b1f72
ms.openlocfilehash: a7c6714218b5891e078e750a974faed274e113c9
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023599"
---
# <a name="data-exchange-for-record-views---mfc-data-access"></a>Intercambio de datos para vistas de registros (acceso a datos MFC)

Cuando usas [Agregar clase](../mfc/reference/adding-an-mfc-odbc-consumer.md) para asignar los controles en el recurso de plantilla de cuadro de diálogo de una vista de registros a los campos de un conjunto de registros, el marco de trabajo administra el intercambio de datos en ambas direcciones: desde el conjunto de registros a los controles y desde los controles al conjunto de registros. Si utiliza el mecanismo DDX, no tiene que escribir por su cuenta el código para transferir los datos en ambos sentidos.

DDX para vistas de registros funciona junto con [RFX](../data/odbc/record-field-exchange-rfx.md) para conjuntos de registros de la clase `CRecordset` (ODBC).  RFX mueve datos entre el registro actual del origen de datos y los miembros de datos de campo de un objeto de conjunto de registros. DDX mueve los datos de los miembros de datos de campo a los controles del formulario. Esta combinación rellena los controles del formulario al principio y a medida que el usuario se desplaza por los registros. Pueden también devolver los datos actualizados al conjunto de registros y, a continuación, moverlos al origen de datos.

En la siguiente ilustración se muestra la relación entre DDX y RFX para vistas de registros.

![Cuadro de diálogo&#45;intercambio de datos y registro&#45;el intercambio de campos](../data/media/vc37xt1.gif "diálogo&#45;intercambio de datos y registro&#45;el intercambio de campos")<br/>
Intercambio de datos de cuadro de diálogo e intercambio de campos de registros

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../mfc/dialog-data-exchange-and-validation.md). Para obtener más información sobre RFX, consulte [intercambio de campos de registros (RFX)](../data/odbc/record-field-exchange-rfx.md).

## <a name="see-also"></a>Vea también

[Vistas de registros (acceso a datos MFC)](../data/record-views-mfc-data-access.md)<br/>
[Lista de controladores ODBC](../data/odbc/odbc-driver-list.md)