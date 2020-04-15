---
title: Clases y subprocesos de ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
ms.openlocfilehash: aaf54a3a1d616cde5742dad45955bd415f612d60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368688"
---
# <a name="odbc-classes-and-threads"></a>Clases y subprocesos de ODBC

A partir de MFC 4.2, hay compatibilidad con multithreading para las clases ODBC de MFC. Tenga en cuenta, sin embargo, que MFC no proporciona compatibilidad con multithreading para las clases DAO.

La compatibilidad con multithreading para las clases ODBC tiene algunas limitaciones. Dado que estas clases ajustan la API ODBC, están restringidas a la compatibilidad con multiproceso de los componentes en los que se compilan. Por ejemplo, muchos controladores ODBC no son seguros para subprocesos; Por lo tanto, las clases ODBC de MFC no son seguras para subprocesos si las usa con uno de estos controladores. Debe comprobar si el controlador en particular es seguro para subprocesos.

Al crear una aplicación multiproceso, debe tener mucho cuidado al usar varios subprocesos para manipular el mismo objeto. Por ejemplo, el `CRecordset` uso del mismo objeto en dos subprocesos puede causar problemas al recuperar datos; una operación de recuperación en un subproceso podría sobrescribir los datos capturados en el otro subproceso. Un uso más común de las clases ODBC `CDatabase` de MFC en subprocesos independientes es `CRecordset` compartir un objeto abierto entre subprocesos para usar la misma conexión ODBC, con un objeto independiente en cada subproceso. Tenga en cuenta que no `CDatabase` debe `CRecordset` pasar un objeto sin abrir a un objeto en otro subproceso.

> [!NOTE]
> Si debe tener varios subprocesos manipular el mismo objeto, debe implementar los mecanismos de sincronización adecuados, como secciones críticas. Tenga en cuenta que `Open`ciertas operaciones, como , no están protegidas. Debe asegurarse de que no se llamará a estas operaciones simultáneamente desde subprocesos independientes.

Para obtener más información sobre la creación de aplicaciones multiproceso, vea Temas de [multiproceso](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

## <a name="see-also"></a>Consulte también

[Conectividad de base de datos abierta (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Programación de acceso a datos (MFC/ATL)](../../data/data-access-programming-mfc-atl.md)
