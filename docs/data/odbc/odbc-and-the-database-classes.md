---
title: ODBC y las clases de base de datos
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
ms.openlocfilehash: 7c69f49cbe233eb0782fdaa9767ea55f4d04203c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213207"
---
# <a name="odbc-and-the-database-classes"></a>ODBC y las clases de base de datos

Las clases de base de datos ODBC de MFC encapsulan las llamadas de función de la API de ODBC que normalmente se realizarían en las funciones miembro de las clases [CDatabase](../../mfc/reference/cdatabase-class.md) y [CRecordset](../../mfc/reference/crecordset-class.md) . Por ejemplo, las clases de base de datos administran las secuencias de llamadas ODBC complejas, el enlace de registros devueltos a ubicaciones de almacenamiento, la administración de condiciones de error y otras operaciones. Como resultado, se usa una interfaz de clase considerablemente más sencilla para manipular los registros a través de un objeto de conjunto de registros.

> [!NOTE]
>  Mediante las clases ODBC de MFC, como se describe en este tema, o las clases DAO de MFC se puede tener acceso a los orígenes de datos ODBC.

Aunque las clases de base de datos encapsulan la funcionalidad ODBC, no proporcionan una asignación uno a uno de las funciones de la API de ODBC. Las clases de base de datos proporcionan un nivel más alto de abstracción, modelado después de los objetos de acceso a datos que se encuentran en Microsoft Access y Microsoft Visual Basic. Para obtener más información, vea [ODBC y MFC](../../data/odbc/odbc-and-mfc.md).

## <a name="see-also"></a>Consulte también

[Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)
