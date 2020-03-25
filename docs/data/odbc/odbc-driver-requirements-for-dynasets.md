---
title: Requisitos del controlador ODBC para conjuntos de registros dinámicos
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, dynasets
- drivers, for dynasets
- drivers, ODBC
- recordsets, dynasets
- dynasets
- ODBC drivers, dynasets
ms.assetid: 585cc67b-4d92-404b-9903-d769cd17badc
ms.openlocfilehash: 3507a5ee7dcfb8bf4f4eee12ef9264c16ad904c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213114"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>Requisitos del controlador ODBC para conjuntos de registros dinámicos

En las clases de base de datos ODBC de MFC, los dynasets son conjuntos de registros con propiedades dinámicas; permanecen sincronizados con el origen de datos de ciertas maneras. Los dynasets de MFC (pero no los conjuntos de registros solo hacia delante) requieren un controlador ODBC con la conformidad de la API de nivel 2. Si el controlador del [origen de datos](../../data/odbc/data-source-odbc.md) se ajusta al conjunto de API de nivel 1, todavía puede usar instantáneas actualizables y de solo lectura y conjuntos de registros solo hacia delante, pero no dynasets. Sin embargo, un controlador de nivel 1 puede admitir dynasets si admite la captura extendida y los cursores controlados por conjunto de claves.

En la terminología de ODBC, los conjuntos de registros dinámicos y las instantáneas se denominan cursores. Un cursor es un mecanismo que se usa para realizar un seguimiento de su posición en un conjunto de registros. Para obtener más información sobre los requisitos de controladores para dynasets, vea [Dynaset](../../data/odbc/dynaset.md). Para obtener más información sobre los cursores, vea el SDK de [Conectividad abierta de bases de datos (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc) en la documentación de MSDN.

> [!NOTE]
>  En el caso de los conjuntos de registros actualizables, el controlador ODBC debe admitir instrucciones Update posicionadas o la función de la API de ODBC `::SQLSetPos`. Si se admiten ambos, MFC utiliza `::SQLSetPos` para mayor eficacia. Como alternativa, en el caso de las instantáneas, puede usar la biblioteca de cursores, que proporciona la compatibilidad necesaria para las instantáneas actualizables (cursores estáticos y instrucciones Update posicionadas).

## <a name="see-also"></a>Consulte también

[Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)
