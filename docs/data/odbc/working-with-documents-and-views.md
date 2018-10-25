---
title: Trabajar con documentos y vistas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], documents
- MFC [C++], views
- views [C++], MFC
- documents [C++], MFC
ms.assetid: 349b142d-1c5a-4b99-9de4-241e41d3d2f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c3879c6a29f95cc908d12c0b899214b521f46686
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060448"
---
# <a name="working-with-documents-and-views"></a>Trabajar con documentos y vistas

La biblioteca Microsoft Foundation Classes (MFC) se basa en una arquitectura documento/vista para muchas de sus características. Normalmente, un documento almacena los datos y una vista muestra en el área de cliente de una ventana de marco y administra la interacción del usuario con los datos. La vista se comunica con el documento para obtener y actualizar los datos. Puede usar las clases de base de datos con el marco de trabajo o sin él.

Para obtener más información sobre cómo usar las clases de base de datos en el marco de trabajo, consulte [MFC: utilizar clases de base de datos con documentos y vistas](../../data/mfc-using-database-classes-with-documents-and-views.md).

De forma predeterminada, el Asistente para aplicaciones MFC crea una aplicación de esqueleto sin soporte de la base de datos. Sin embargo, puede seleccionar opciones para incluir compatibilidad con la base de datos mínima o una compatibilidad más completa basada en formularios. Para obtener más información sobre las opciones del Asistente para aplicaciones, consulte [soporte técnico de la base de datos, Asistente para aplicaciones MFC](../../mfc/reference/database-support-mfc-application-wizard.md).

También puede usar las clases de base de datos sin usar la arquitectura documento/vista completa. Para obtener más información, consulte [MFC: utilizar clases de base de datos sin documentos y vistas](../../data/mfc-using-database-classes-without-documents-and-views.md).

## <a name="see-also"></a>Vea también

[ODBC y MFC](../../data/odbc/odbc-and-mfc.md)