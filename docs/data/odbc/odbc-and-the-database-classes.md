---
title: ODBC y las clases de base de datos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e3041a4fc027a8786fb62db7df6eaf486633ce97
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-and-the-database-classes"></a>ODBC y las clases de base de datos
Las clases de base de datos ODBC de MFC encapsulan las llamadas a funciones API de ODBC que normalmente haría usted mismo en el miembro de las funciones de la [CDatabase](../../mfc/reference/cdatabase-class.md) y [CRecordset](../../mfc/reference/crecordset-class.md) clases. Por ejemplo, las secuencias de llamadas ODBC complejas, el enlace de registros devueltos a ubicaciones de almacenamiento, control de las condiciones de error y otras operaciones se administran automáticamente por las clases de base de datos. Como resultado, utilice una interfaz de clase bastante más sencilla para manipular registros mediante un objeto de conjunto de registros.  
  
> [!NOTE]
>  Mediante las clases ODBC de MFC, como se describe en este tema, o las clases DAO de MFC se puede tener acceso a los orígenes de datos ODBC.  
  
 Aunque las clases de base de datos encapsulan la funcionalidad ODBC, no proporcionan una asignación unívoca de funciones de la API de ODBC. Las clases de base de datos proporcionan un mayor nivel de abstracción, que se modela después de encontraron los objetos de acceso a datos en Microsoft Access y Microsoft Visual Basic. Para obtener más información, consulte [ODBC y MFC](../../data/odbc/odbc-and-mfc.md).  
  
## <a name="see-also"></a>Vea también  
 [Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)