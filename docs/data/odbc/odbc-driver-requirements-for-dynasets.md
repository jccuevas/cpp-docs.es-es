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
ms.openlocfilehash: c612e8ea91882a6e744a8f47afe0decbeba85358
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367212"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>Requisitos del controlador ODBC para conjuntos de registros dinámicos

En las clases de base de datos ODBC de MFC, los conjuntos de registros dinámicos son conjuntos de registros con propiedades dinámicas; permanecen sincronizados con el origen de datos de ciertas maneras. Los conjuntos de registros dinámicos de MFC (pero no los conjuntos de registros de solo avance) requieren un controlador ODBC con conformidad de la API de nivel 2. Si el controlador del origen de [datos](../../data/odbc/data-source-odbc.md) se ajusta al conjunto de API de nivel 1, puede seguir utilizando instantáneas actualizables y de solo lectura y conjuntos de registros de solo avance, pero no conjuntos de registros dinámicos. Sin embargo, un controlador de nivel 1 puede admitir conjuntos de registros dinámicos si admite la obtención extendida y cursores controlados por conjuntos de claves.

En la terminología ODBC, los conjuntos de registros dinámicos y las instantáneas se conocen como cursores. Un cursor es un mecanismo utilizado para realizar un seguimiento de su posición en un conjunto de registros. Para obtener más información acerca de los requisitos del controlador para conjuntos de registros dinámicos, vea [Dynaset](../../data/odbc/dynaset.md). Para obtener más información acerca de los cursores, vea el SDK de conectividad abierta de base de [datos (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc) en la documentación de MSDN.

> [!NOTE]
> Para conjuntos de registros actualizables, el controlador ODBC `::SQLSetPos` debe admitir instrucciones de actualización posicionadas o la función de API ODBC. Si se admiten `::SQLSetPos` ambos, MFC se usa para la eficiencia. Como alternativa, para las instantáneas, puede utilizar la biblioteca de cursores, que proporciona la compatibilidad necesaria para las instantáneas actualizables (cursores estáticos e instrucciones de actualización posicionadas).

## <a name="see-also"></a>Consulte también

[Fundamentos de ODBC](../../data/odbc/odbc-basics.md)
