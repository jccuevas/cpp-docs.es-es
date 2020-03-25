---
title: Clases y subprocesos de ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
ms.openlocfilehash: 8cb5df605bef31e177e976798f975bb4ca14ced7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213201"
---
# <a name="odbc-classes-and-threads"></a>Clases y subprocesos de ODBC

A partir de MFC 4,2, existe compatibilidad con multithreading para las clases ODBC de MFC. Tenga en cuenta, sin embargo, que MFC no proporciona compatibilidad con multithreading para las clases DAO.

La compatibilidad con multithreading para las clases ODBC tiene algunas limitaciones. Dado que estas clases encapsulan la API de ODBC, están restringidas a la compatibilidad con multithreading de los componentes en los que se compilan. Por ejemplo, muchos controladores ODBC no son seguros para subprocesos; por lo tanto, las clases ODBC de MFC no son seguras para subprocesos si se usan con uno de estos controladores. Debe comprobar si el controlador concreto es seguro para subprocesos.

Al crear una aplicación multiproceso, debe tener mucho cuidado al usar varios subprocesos para manipular el mismo objeto. Por ejemplo, si se usa el mismo objeto `CRecordset` en dos subprocesos, podrían producirse problemas al recuperar datos; una operación de captura en un subproceso podría sobrescribir los datos capturados en el otro subproceso. Un uso más común de las clases ODBC de MFC en subprocesos independientes es compartir un objeto de `CDatabase` abierto entre subprocesos para utilizar la misma conexión ODBC, con un objeto de `CRecordset` independiente en cada subproceso. Tenga en cuenta que no debe pasar un objeto `CDatabase` no abierto a un objeto `CRecordset` en otro subproceso.

> [!NOTE]
>  Si debe tener varios subprocesos manipulando el mismo objeto, debe implementar los mecanismos de sincronización adecuados, como las secciones críticas. Tenga en cuenta que ciertas operaciones, como `Open`, no están protegidas. Debe asegurarse de que estas operaciones no se llamarán simultáneamente desde subprocesos independientes.

Para obtener más información sobre la creación de aplicaciones multiproceso, vea [temas de multithreading](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

## <a name="see-also"></a>Consulte también

[Conectividad abierta de bases de datos (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Programación del acceso a datos (MFC/ATL)](../../data/data-access-programming-mfc-atl.md)
