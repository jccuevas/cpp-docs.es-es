---
title: 'Origen de datos: Determinar el esquema del origen de datos (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC data sources [C++], schema
- schemas [C++], data sources
- data sources [C++], determining schema
ms.assetid: 17284acb-eb10-4f27-9944-ad1d973c0b05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b5ba9789226e54c9607e85caaa5e8af3f157f02d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052643"
---
# <a name="data-source-determining-the-schema-of-the-data-source-odbc"></a>Origen de datos: Determinar el esquema del origen de datos (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

Para configurar los miembros de datos en su `CRecordset` objetos, deberá conocer el esquema del origen de datos al que se está conectando. Determinar el esquema de un origen de datos implica la obtención de una lista de las tablas del origen de datos, una lista de las columnas de cada tabla, el tipo de datos de cada columna y la existencia de los índices.

## <a name="see-also"></a>Vea también

[Origen de datos (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[Origen de datos: Administrar conexiones (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)