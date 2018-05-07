---
title: Clases DAO | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.data
dev_langs:
- C++
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f43595ca5f688372a70999231ceebec5282cd3b6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="dao-classes"></a>Clases de DAO
Estas clases funcionan con las otras clases de framework de aplicación para proporcionar acceso fácil a las bases de datos de objeto de acceso a datos (DAO), que usan el mismo motor de base de datos como Microsoft Visual Basic y Microsoft Access. Las clases DAO también pueden tener acceso a una amplia variedad de bases de datos para los que están disponibles los controladores de conectividad abierta de base de datos (ODBC).  
  
 Programas que utilizan las bases de datos DAO tendrá al menos un `CDaoDatabase` objeto y un `CDaoRecordset` objeto.  
  
> [!NOTE]
>  Los asistentes y el entorno de Visual C++ ya no admiten DAO (aunque las clases DAO están incluidas y puede seguir usándolos). Microsoft recomienda utilizar ODBC para nuevos proyectos MFC. Solo debería utilizar DAO para mantener las aplicaciones existentes.  
  
 [CDaoWorkspace](../mfc/reference/cdaoworkspace-class.md)  
 Administra una sesión de base de datos con nombre, protegida por contraseña de inicio de sesión a cierre de sesión. Mayoría de los programas utilice el área de trabajo de forma predeterminada.  
  
 [CDaoDatabase](../mfc/reference/cdaodatabase-class.md)  
 Una conexión a una base de datos a través del cual se puede operar en los datos.  
  
 [CDaoRecordset](../mfc/reference/cdaorecordset-class.md)  
 Representa un conjunto de registros seleccionados de un origen de datos.  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 Una vista que muestra registros de una base de datos en controles.  
  
 [CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)  
 Representa una definición de consulta, normalmente uno guardado en una base de datos.  
  
 [CDaoTableDef](../mfc/reference/cdaotabledef-class.md)  
 Representa la definición almacenada de una tabla base o una tabla asociada.  
  
 [CDaoException](../mfc/reference/cdaoexception-class.md)  
 Representa una condición de excepción que surge de las clases DAO.  
  
 [CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)  
 Admite las rutinas de intercambio de campos del registro (DFX) de DAO utilizadas por las clases de base de datos DAO. Normalmente, no utilizará directamente esta clase.  
  
## <a name="related-classes"></a>Clases relacionadas  
 [CLongBinary](../mfc/reference/clongbinary-class.md)  
 Encapsula un identificador de almacenamiento para un objeto binario grande (BLOB), como un mapa de bits. `CLongBinary` los objetos se usan para administrar objetos de gran cantidad de datos almacenados en tablas de base de datos.  
  
 [COleCurrency](../mfc/reference/colecurrency-class.md)  
 Contenedor para el tipo de automatización OLE **moneda**, un tipo aritmético punto fijo, con 15 dígitos que hay delante del separador decimal y 4 dígitos después.  
  
 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)  
 Contenedor para el tipo de automatización OLE **fecha**. Representa valores de fecha y hora.  
  
 [COleVariant](../mfc/reference/colevariant-class.md)  
 Contenedor para el tipo de automatización OLE **VARIANT**. Datos de **VARIANT**s pueden almacenarse en muchos formatos.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

