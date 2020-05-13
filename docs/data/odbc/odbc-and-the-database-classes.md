---
title: ODBC y las clases de base de datos
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
ms.openlocfilehash: 6511aab9bb048882fe9c3398dd17f769eb16220c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320061"
---
# <a name="odbc-and-the-database-classes"></a>ODBC y las clases de base de datos

Las clases de base de datos ODBC de MFC encapsulan las llamadas de función de la API ODBC que normalmente se haría en las funciones miembro de las clases [CDatabase](../../mfc/reference/cdatabase-class.md) y [CRecordset.](../../mfc/reference/crecordset-class.md) Por ejemplo, las clases de base de datos administran automáticamente las complejas secuencias de llamadas ODBC, el enlace de registros devueltos a ubicaciones de almacenamiento, el control de condiciones de error y otras operaciones. Como resultado, se utiliza una interfaz de clase considerablemente más sencilla para manipular registros a través de un objeto de conjunto de registros.

> [!NOTE]
> Mediante las clases ODBC de MFC, como se describe en este tema, o las clases DAO de MFC se puede tener acceso a los orígenes de datos ODBC.

Aunque las clases de base de datos encapsulan la funcionalidad ODBC, no proporcionan una asignación uno a uno de las funciones de la API ODBC. Las clases de base de datos proporcionan un mayor nivel de abstracción, modelado a partir de objetos de acceso a datos que se encuentran en Microsoft Access y Microsoft Visual Basic. Para obtener más información, vea [ODBC y MFC](../../data/odbc/odbc-and-mfc.md).

## <a name="see-also"></a>Consulte también

[Fundamentos de ODBC](../../data/odbc/odbc-basics.md)
