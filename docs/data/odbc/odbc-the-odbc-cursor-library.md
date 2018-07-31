---
title: 'ODBC: Biblioteca de cursores ODBC | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 064683c3905e7ad8ba1e405bd3963832c65cff57
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340409"
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC: Biblioteca de cursores ODBC
En este tema se describe la biblioteca de cursores ODBC y se explica cómo usarlo. Para obtener más información, consulte:  
  
-   [Controladores ODBC de nivel 1 y de biblioteca de cursores](#_core_the_cursor_library_and_level_1_odbc_drivers)  
  
-   [Actualizaciones por posición y las columnas de marca de tiempo](#_core_positioned_updates_and_timestamp_columns)  
  
-   [Uso de la biblioteca de cursores](#_core_using_the_cursor_library)  
  
 La biblioteca de cursores ODBC es una biblioteca de vínculos dinámicos (DLL) que se encuentra entre el Administrador de controladores ODBC y el controlador. En términos de ODBC, un controlador conserva un cursor para realizar un seguimiento de su posición en el conjunto de registros. El cursor marca la posición en el conjunto de registros a los que ya se ha desplazado, el registro actual.  
  
##  <a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a> Controladores ODBC de nivel 1 y de biblioteca de cursores  
 La biblioteca de cursores ODBC proporciona las siguientes capacidades nuevas de controladores de nivel 1:  
  
-   Desplazamiento hacia delante y hacia atrás. Los controladores de nivel 2 no necesitan la biblioteca de cursores porque ya se puede desplazables.  
  
-   Compatibilidad con instantáneas. La biblioteca de cursores administra un búfer que contiene los registros de la instantánea. Este búfer refleja el programa eliminaciones y modificaciones de registros pero no las adiciones, eliminaciones o ediciones de otros usuarios. Por lo tanto, la instantánea está tan actualizada como búfer de la biblioteca de cursores. El búfer no refleja sus propias aportaciones hasta que llame a `Requery`. Conjuntos de registros dinámicos no use la biblioteca de cursores.  
  
 La biblioteca de cursores asigna instantáneas (cursores estáticos) incluso si no se admiten normalmente por el controlador. Si el controlador ya es compatible con los cursores estáticos, no es necesario cargar la biblioteca de cursores para obtener compatibilidad con instantáneas. Si usa la biblioteca de cursores, puede usar solo las instantáneas y los conjuntos de registros solo hacia delante. Si el controlador admite conjuntos de registros dinámicos (cursores KEYSET_DRIVEN) y desea usarlas, no debe usar la biblioteca de cursores. Si desea utilizar instantáneas y conjuntos de registros dinámicos, se debe basar en dos diferentes `CDatabase` objetos (dos conexiones distintas) a menos que el controlador es compatible con ambos.  
  
##  <a name="_core_positioned_updates_and_timestamp_columns"></a> Actualizaciones por posición y las columnas de marca de tiempo  
  
> [!NOTE]
>  Mediante las clases ODBC de MFC, como se describe en este tema, o las clases DAO de MFC se puede tener acceso a los orígenes de datos ODBC.  
  
> [!NOTE]
>  Si el controlador ODBC admite `SQLSetPos`, que MFC utiliza si está disponible, este tema no se aplica a usted.  
  
 La mayoría de los controladores de nivel 1 no admiten actualizaciones posicionadas. Estos controladores se basan en la biblioteca de cursores para emular las capacidades de los controladores de nivel 2 en este sentido. La biblioteca de cursores emula la compatibilidad de actualización posicionada realizando una actualización por búsqueda en los campos que no cambian.  
  
 En algunos casos, un conjunto de registros puede contener una columna de marca de tiempo como uno de esos campos que no cambian. Surgen dos problemas en el uso de conjuntos de registros MFC con tablas que contienen columnas de marca de tiempo.  
  
 El primer problema refiere a las instantáneas actualizables en tablas con columnas de marca de tiempo. Si la tabla a la que está enlazado a la instantánea contiene una columna de marca de tiempo, se debe llamar a `Requery` después de llamar a `Edit` y `Update`. De lo contrario, es posible que no pueda editar de nuevo el mismo registro. Cuando se llama a `Edit` y, a continuación, `Update`, el registro se escribe en el origen de datos y se actualiza la columna de marca de tiempo. Si no se llama `Requery`, el valor de marca de tiempo para el registro de la instantánea ya no coincide con la marca de tiempo correspondiente en el origen de datos. Cuando se vuelva a intentar actualizar el registro, el origen de datos podría no permitir la actualización debido a la falta de coincidencia.  
  
 El segundo problema refiere a las limitaciones de la clase [CTime](../../atl-mfc-shared/reference/ctime-class.md) cuando se usa con el `RFX_Date` función para transferir información de fecha y hora a o desde una tabla. Procesando la `CTime` objeto supone una sobrecarga en forma de procesamiento adicional intermedio durante la transferencia de datos. El intervalo de fechas de `CTime` objetos también podrían limitar demasiado para algunas aplicaciones. Una nueva versión de la `RFX_Date` función toma un ODBC *TIMESTAMP_STRUCT* parámetro en lugar de un `CTime` objeto. Para obtener más información, consulte `RFX_Date` en [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md) en el *referencia de MFC*.  

  
##  <a name="_core_using_the_cursor_library"></a> Uso de la biblioteca de cursores  
 Cuando se conecta a un origen de datos, mediante una llamada a [CDatabase:: OpenEx](../../mfc/reference/cdatabase-class.md#openex) o [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) , puede especificar si desea utilizar la biblioteca de cursores para el origen de datos. Si va a crear instantáneas en ese origen de datos, especifique el `CDatabase::useCursorLib` opción el `dwOptions` parámetro `OpenEx` o especifique "true" para el *bUseCursorLib* parámetro `Open` (el valor predeterminado es TRUE). Si el controlador ODBC admite conjuntos de registros dinámicos y desea abrir conjuntos de registros dinámicos en el origen de datos, no utilice la biblioteca de cursores (enmascaran algunas funciones de controlador necesarios para conjuntos de registros dinámicos). En ese caso, no especifique `CDatabase::useCursorLib` en `OpenEx` o especifique FALSE para el *bUseCursorLib* parámetro `Open`.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)