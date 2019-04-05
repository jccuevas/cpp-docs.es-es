---
title: 'Origen de datos: Determinar el esquema del origen de datos (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources [C++], schema
- schemas [C++], data sources
- data sources [C++], determining schema
ms.assetid: 17284acb-eb10-4f27-9944-ad1d973c0b05
ms.openlocfilehash: c419a3ac2d870e6a85675492ee6c9b726427a0e9
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59040035"
---
# <a name="data-source-determining-the-schema-of-the-data-source-odbc"></a>Origen de datos: Determinar el esquema del origen de datos (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

Para configurar los miembros de datos en su `CRecordset` objetos, deberá conocer el esquema del origen de datos al que se está conectando. Determinar el esquema de un origen de datos implica la obtención de una lista de las tablas del origen de datos, una lista de las columnas de cada tabla, el tipo de datos de cada columna y la existencia de los índices.

## <a name="see-also"></a>Vea también

[Origen de datos (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[Origen de datos: Administrar conexiones (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)