---
title: Clases ODBC y subprocesos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dedd1f03bf14e0513f9f76a1e292b9180e4d60db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090593"
---
# <a name="odbc-classes-and-threads"></a>Clases y subprocesos de ODBC
Empezando por MFC 4.2, no hay compatibilidad con multithreading para las clases ODBC de MFC. Sin embargo, tenga en cuenta que MFC no proporciona compatibilidad con multithreading para las clases DAO.  
  
 La compatibilidad con multithreading para las clases ODBC tiene algunas limitaciones. Dado que estas clases ajustan a la API de ODBC, están limitadas a la compatibilidad con multithreading de los componentes en el que se generan. Por ejemplo, muchos controladores ODBC no son seguros para subprocesos; por lo tanto, las clases ODBC de MFC no son subprocesos si usa uno de estos controladores. Debe comprobar si el controlador en particular es segura para subprocesos.  
  
 Al crear una aplicación multiproceso, debe tener mucho cuidado al utilizar varios subprocesos para manipular el mismo objeto. Por ejemplo, si se usa el mismo `CRecordset` objeto en dos subprocesos puede provocar problemas cuando se recuperan datos; una operación de búsqueda en un subproceso podría sobrescribir los datos capturados en el otro subproceso. Un uso más común de las clases ODBC de MFC en subprocesos independientes es compartir abierto `CDatabase` objeto entre varios subprocesos para utilizar la misma conexión ODBC, con otro `CRecordset` objeto en cada subproceso. Tenga en cuenta que no se debe pasar una sin abrir `CDatabase` el objeto a un `CRecordset` objeto en otro subproceso.  
  
> [!NOTE]
>  Si es necesario tener varios subprocesos manipular el mismo objeto, debe implementar los mecanismos de sincronización apropiada, por ejemplo, secciones críticas. Tenga en cuenta que algunas operaciones, como **abiertos**, no están protegidos. Debe asegurarse de que estas operaciones no se llamará simultáneamente desde subprocesos independientes.  
  
 Para obtener más información acerca de cómo crear aplicaciones multiproceso, consulte [temas de Multithreading](../../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
## <a name="see-also"></a>Vea también  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [Acceso a los datos de programación (MFC/ATL)](../../data/data-access-programming-mfc-atl.md)