---
title: ODBC y las clases de base de datos
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
ms.openlocfilehash: 709608098a0c979cd7816ae4f8012372099ef52d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575609"
---
# <a name="odbc-and-the-database-classes"></a>ODBC y las clases de base de datos

Las clases de base de datos ODBC de MFC encapsulan las llamadas de función de la API de ODBC que normalmente haría por sí mismo en el miembro de las funciones de la [CDatabase](../../mfc/reference/cdatabase-class.md) y [CRecordset](../../mfc/reference/crecordset-class.md) clases. Por ejemplo, las secuencias complejas de llamada ODBC, enlace de registros devueltos a las ubicaciones de almacenamiento, el control de las condiciones de error y otras operaciones se administran automáticamente por las clases de base de datos. Como resultado, utiliza una interfaz de clase bastante más sencilla para manipular registros mediante un objeto de conjunto de registros.

> [!NOTE]
>  Mediante las clases ODBC de MFC, como se describe en este tema, o las clases DAO de MFC se puede tener acceso a los orígenes de datos ODBC.

Aunque las clases de base de datos encapsulan la funcionalidad ODBC, no proporcionan una asignación uno a uno de las funciones de API de ODBC. Las clases de base de datos proporcionan un mayor nivel de abstracción, que se modela después de encontraron los objetos de acceso a datos en Microsoft Access y Microsoft Visual Basic. Para obtener más información, consulte [ODBC y MFC](../../data/odbc/odbc-and-mfc.md).

## <a name="see-also"></a>Vea también

[Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)