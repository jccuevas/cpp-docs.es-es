---
title: 'ODBC: Biblioteca de cursores ODBC | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- cursor library [ODBC]
- snapshots, support in ODBC
- timestamps, ODBC timestamp columns
- ODBC cursor library [ODBC]
- static cursors
- ODBC drivers, Level 1
- ODBC drivers, cursor support
- positioned updates
- cursors, ODBC cursor library
- Level 1 ODBC drivers
- cursor library [ODBC], snapshots
- ODBC, timestamp
- positioning cursors
ms.assetid: 6608db92-82b1-4164-bb08-78153c227be3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3d849580ce3e9b264c854633c6bb9f274874c21d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC: Biblioteca de cursores ODBC
Este tema describe la biblioteca de cursores ODBC y explica cómo usarlo. Para obtener más información, consulte:  
  
-   [Biblioteca de cursores y nivel 1 controladores ODBC](#_core_the_cursor_library_and_level_1_odbc_drivers)  
  
-   [Actualizaciones por posición y las columnas de marca de tiempo](#_core_positioned_updates_and_timestamp_columns)  
  
-   [Uso de la biblioteca de cursores](#_core_using_the_cursor_library)  
  
 La biblioteca de cursores ODBC es una biblioteca de vínculos dinámicos (DLL) que se encuentra entre el Administrador de controladores ODBC y el controlador. En términos de ODBC, un controlador conserva un cursor para realizar un seguimiento de su posición en el conjunto de registros. El cursor marca la posición en el conjunto de registros a los que ya se ha desplazado: el registro actual.  
  
##  <a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a>Biblioteca de cursores y nivel 1 controladores ODBC  
 La biblioteca de cursores ODBC proporciona a los controladores de nivel 1 las siguientes capacidades nuevas:  
  
-   Desplazamiento hacia delante y hacia atrás. Controladores de nivel 2 no necesitan la biblioteca de cursores porque ya están desplazables.  
  
-   Compatibilidad con instantáneas. La biblioteca de cursores administra un búfer que contiene los registros de la instantánea. Este búfer refleja el programa eliminaciones y modificaciones a registros pero no las adiciones, eliminaciones o modificaciones de otros usuarios. Por lo tanto, la instantánea está tan actualizada como búfer de la biblioteca de cursores. El búfer también no refleja las adiciones personales hasta que se llama **Requery**. Conjuntos de registros dinámicos no utilizan la biblioteca de cursores.  
  
 La biblioteca de cursores ofrece instantáneas (cursores estáticos) aunque no se admiten normalmente por el controlador. Si el controlador ya es compatible con los cursores estáticos, no es necesario cargar la biblioteca de cursores para obtener compatibilidad con instantáneas. Si utiliza la biblioteca de cursores, puede utilizar solo las instantáneas y conjuntos de registros solo hacia delante. Si el controlador es compatible con conjuntos de registros dinámicos (cursores KEYSET_DRIVEN) y desea utilizarlos, no debe usar la biblioteca de cursores. Si desea utilizar instantáneas y conjuntos de registros dinámicos, se debe basar en dos diferentes `CDatabase` objetos (dos conexiones distintas) a menos que el controlador es compatible con ambos.  
  
##  <a name="_core_positioned_updates_and_timestamp_columns"></a>Actualizaciones por posición y las columnas de marca de tiempo  
  
> [!NOTE]
>  Mediante las clases ODBC de MFC, como se describe en este tema, o las clases DAO de MFC se puede tener acceso a los orígenes de datos ODBC.  
  
> [!NOTE]
>  Si el controlador ODBC admite **SQLSetPos**, que MFC utiliza si está disponible, este tema no se aplica a usted.  
  
 La mayoría de los controladores de nivel 1 no admiten actualizaciones por posición. Estos controladores se basan en la biblioteca de cursores para emular las capacidades de los controladores de nivel 2 en este sentido. La biblioteca de cursores emula la compatibilidad de actualización posicionada realizando una actualización por búsqueda en los campos que no cambian.  
  
 En algunos casos, un conjunto de registros puede contener una columna de marca de tiempo como uno de dichos campos inalterados. Surgen dos problemas de uso de conjuntos de registros MFC con tablas que contienen columnas de marca de tiempo.  
  
 El primer problema está relacionado con las instantáneas actualizables en tablas con columnas de marca de tiempo. Si la tabla a la que está enlazado la instantánea contiene una columna de marca de tiempo, debe llamar a **Requery** después de llamar a **editar** y **actualización**. De lo contrario, es posible que no pueda editar de nuevo el mismo registro. Cuando se llama a **editar** y, a continuación, **actualización**, el registro se escribe en el origen de datos y se actualiza la columna de marca de tiempo. Si no se llama **Requery**, el valor de marca de tiempo para el registro de la instantánea ya no coincide con la marca de tiempo correspondiente en el origen de datos. Al intentar actualizar el registro de nuevo, el origen de datos podría no permitir la actualización debido a la falta de coincidencia.  
  
 El segundo problema está relacionado con las limitaciones de la clase [CTime](../../atl-mfc-shared/reference/ctime-class.md) cuando se usa con el `RFX_Date` función para transferir información de fecha y hora a o desde una tabla. Procesar la `CTime` objeto supone una sobrecarga en forma de procesamiento adicional intermedio durante la transferencia de datos. El intervalo de fechas de `CTime` objetos también podrían limitar demasiado para algunas aplicaciones. Una nueva versión de la `RFX_Date` función toma un ODBC **TIMESTAMP_STRUCT** parámetro en lugar de un `CTime` objeto. Para obtener más información, consulte `RFX_Date` en [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md) en el *referencia de MFC*.  

  
##  <a name="_core_using_the_cursor_library"></a>Uso de la biblioteca de cursores  
 Cuando se conecta a un origen de datos, mediante una llamada a [CDatabase:: OpenEx](../../mfc/reference/cdatabase-class.md#openex) o [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) , puede especificar si desea utilizar la biblioteca de cursores para el origen de datos. Si va a crear instantáneas en dicho origen de datos, especifique la **CDatabase:: useCursorLib** opción en el `dwOptions` parámetro `OpenEx` o especificar **TRUE** para el  **bUseCursorLib** parámetro **abiertos** (el valor predeterminado es **TRUE**). Si el controlador ODBC admite conjuntos de registros dinámicos y desea abrir conjuntos de registros dinámicos en el origen de datos, no utilice la biblioteca de cursores (enmascara alguna funcionalidad del controlador necesaria para conjuntos de registros dinámicos). En ese caso, no especifique **CDatabase:: useCursorLib** en `OpenEx` o especificar **FALSE** para el **bUseCursorLib** parámetro en **abrir**.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)