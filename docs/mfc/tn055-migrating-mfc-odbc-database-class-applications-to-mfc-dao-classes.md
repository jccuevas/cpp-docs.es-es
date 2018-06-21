---
title: 'TN055: Migrar aplicaciones de clase de base de datos ODBC de MFC a clases DAO de MFC | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.odbc
dev_langs:
- C++
helpviewer_keywords:
- DAO [MFC], migration
- TN055
- migration [MFC], ODBC database applications
- ODBC classes [MFC], DAO classes
- migrating ODBC database applications [MFC]
- porting database applications to DAO
- ODBC [MFC], DAO
- porting ODBC database applications to DAO
- migrating database applications [MFC]
ms.assetid: 0f858bd1-e168-4e2e-bcd1-8debd82856e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c346ca05a72917af615ecd6704a96ff9c190350
ms.sourcegitcommit: 05075fce8a0ed7fddb99f50f3931db966a91450d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/20/2018
ms.locfileid: "36271427"
---
# <a name="tn055-migrating-mfc-odbc-database-class-applications-to-mfc-dao-classes"></a>TN055: Migrar aplicaciones de clase de base de datos ODBC de MFC a clases DAO de MFC
> [!NOTE]
>  El entorno de Visual C++ y los asistentes no admiten DAO (aunque las clases DAO están incluidas y puede seguir usándolos). Microsoft recomienda que utilice [plantillas OLE DB](../data/oledb/ole-db-templates.md) o [ODBC y MFC](../data/odbc/odbc-and-mfc.md) para los nuevos proyectos. Solo debería utilizar DAO para mantener las aplicaciones existentes.  
  
 **Información general**  
  
 En muchos casos puede ser deseable para migrar las aplicaciones que utilizan las clases de base de datos ODBC de MFC a clases de base de datos DAO de MFC. Esta nota técnica detallará la mayoría de las diferencias entre las clases DAO y ODBC de MFC. Teniendo en cuenta las diferencias, no debe estar demasiado difícil de migrar aplicaciones de las clases ODBC de las clases de MFC, si lo desea.  
  
 **¿Por qué migrar de ODBC a DAO**  
  
 Hay una serie de motivos por qué desea migrar aplicaciones de las clases de base de datos de ODBC a las clases de base de datos de DAO, pero la Decisión no es necesariamente obvio o simple. Hay que tener en cuenta es que el motor de base de datos de Microsoft Jet que se usa por DAO puede leer cualquier origen de datos ODBC para que tenga un controlador ODBC. Puede ser más eficaz utilizar las clases de base de datos ODBC o llamar a ODBC directamente por sí mismo, pero el motor de base de datos de Microsoft Jet puede leer los datos ODBC.  
  
 Los casos más sencillos que facilitan la decisión de ODBC o DAO. Por ejemplo, cuando sólo necesita acceso a los datos en un formato que el motor de Microsoft Jet puede leer directamente (formato de Access, formato de Excel etc.) la opción obvia consiste en utilizar las clases de base de datos DAO.  
  
 Casos más complejos se producen cuando los datos existen en un servidor o en una variedad de distintos servidores. En este caso, la decisión de utilizar las clases de base de datos ODBC o las clases de base de datos DAO es difícil. Si desea hacen cosas como combinaciones heterogéneas (combinación de datos de los servidores de varios formatos, como SQL Server y Oracle), a continuación, el motor de base de datos de Microsoft Jet realizará la combinación para en lugar de obligarle a hacer el trabajo necesario si utiliza la base de datos de ODBC Clases u ODBC llama directamente. Si usas un controlador ODBC que admite cursores de controlador, la mejor opción podría ser las clases de base de datos ODBC.  
  
 La opción puede ser complicada, por lo que se desea escribir código de ejemplo para probar el rendimiento de diversos métodos tiene sus necesidades especiales. Esta nota técnica se da por supuesto que ha tomado la decisión de migrar desde las clases de base de datos de ODBC a las clases de base de datos DAO.  
  
 **Similitudes entre las clases de base de datos ODBC y las clases de base de datos DAO de MFC**  
  
 El diseño original de las clases ODBC de MFC se basa en el modelo de objetos DAO que está en uso en Microsoft Access y Microsoft Visual Basic. Esto significa que hay muchas características comunes de las clases ODBC y DAO de MFC, no todas se enumerarán en esta sección. En general, los modelos de programación son los mismos.  
  
 Para resaltar algunas similitudes:  
  
-   Clases ODBC y DAO tienen objetos de base de datos que se administran mediante el sistema de administración de bases de datos (DBMS) subyacente.  
  
-   Ambos tienen objetos de conjunto de registros que representan un conjunto de resultados devueltos de ese DBMS.  
  
-   Los objetos de base de datos y el conjunto de registros DAO tengan miembros casi idénticos a las clases ODBC.  
  
-   Con dos conjuntos de clases, el código para recuperar los datos es idéntico salvo algunos cambios de nombre de objeto y el miembro. Deberá realizar cambios, pero normalmente el proceso es un cambio de nombre sencillo cuando se cambia desde las clases ODBC de clases DAO.  
  
 Por ejemplo, en ambos modelos es el procedimiento para recuperar datos para crear y abrir un objeto de base de datos, crear y abrir un objeto de conjunto de registros y navegar (movimiento) aunque los datos al realizar una operación.  
  
 **Diferencias entre las clases de MFC DAO y ODBC**  
  
 Las clases DAO incluyen más objetos y un conjunto más completo de métodos, pero en esta sección solo se detallará las diferencias en las clases similares y funcionalidad.  
  
 Probablemente las diferencias más obvias entre las clases son los cambios de nombre de las clases similares y funciones globales. La siguiente lista muestra los cambios de nombre de los objetos, métodos y funciones globales asociadas a las clases de base de datos:  
  
|Clase o función|Equivalente en clases DAO de MFC|  
|-----------------------|-----------------------------------|  
|`CDatabase`|`CDaoDatabase`|  
|`CDatabase::ExecuteSQL`|`CDaoDatabase::Execute`|  
|`CRecordset`|`CDaoRecordset`|  
|`CRecordset::GetDefaultConnect`|`CDaoRecordset::GetDefaultDBName`|  
|`CFieldExchange`|`CDaoFieldExchange`|  
|`RFX_Bool`|`DFX_Bool`|  
|`RFX_Byte`|`DFX_Byte`|  
|`RFX_Int`|`DFX_Short`|  
|`RFX_Long`|`DFX_Long`|  
||`DFX_Currency`|  
|`RFX_Single`|`DFX_Single`|  
|`RFX_Double`|`DFX_Double`|  
|**RFX_Date \\\***|**DFX_Date** (`COleDateTime`-según)|  
|`RFX_Text`|`DFX_Text`|  
|`RFX_Binary`|`DFX_Binary`|  
|`RFX_LongBinary`|`DFX_LongBinary`|  
  
 \*    El `RFX_Date` función se basa en `CTime` y **TIMESTAMP_STRUCT**.  
  
 Los cambios más importantes a la funcionalidad que pueden afectar a la aplicación y requieren cambios en el nombre de más de simple se enumeran a continuación.  
  
-   Se cambiaron las constantes y macros que se utilizan para especificar elementos tales como el conjunto de registros de tipo open y opciones de abrir el conjunto de registros.  
  
     Con las clases ODBC de MFC necesarios para definir estas opciones mediante macros o tipos enumerados.  
  
     Con las clases DAO, DAO proporciona la definición de estas opciones en un archivo de encabezado (DBDAOINT. (H). Por lo tanto el tipo de conjunto de registros es un miembro enumerado de `CRecordset`, pero con DAO es una constante en su lugar. Por ejemplo utilice **instantánea** cuando se especifica el tipo de `CRecordset` en ODBC, pero **DB_OPEN_SNAPSHOT** cuando se especifica el tipo de `CDaoRecordset`.  
  
-   El tipo de conjunto de registros predeterminado de `CRecordset` es **instantánea** mientras el tipo de conjunto de registros predeterminado de `CDaoRecordset` es **dynaset** (vea la nota siguiente para un problema adicional acerca de las instantáneas de clase ODBC).  
  
-   ODBC `CRecordset` clase tiene una opción para crear un tipo de conjunto de registros solo hacia delante. En el `CDaoRecordset` (clase), solo avance no es un tipo de conjunto de registros, pero en su lugar una propiedad (u opción) de ciertos tipos de conjuntos de registros.  
  
-   Un conjunto de registros solo de adición al abrir un `CRecordset` objeto significa que los datos del conjunto de registros se pueden leer y anexar. Con `CDaoRecordset` de objeto, la opción de sólo anexar literalmente significa que los datos del conjunto de registros solo pueden ser anexa (y no de lectura).  
  
-   Funciones de miembro de transacción de las clases ODBC son miembros de `CDatabase` y actuar en el nivel de base de datos. En las clases DAO, las funciones de miembro de la transacción son miembros de una clase de nivel superior (`CDaoWorkspace`) y, por tanto, puede afectar a varias `CDaoDatabase` los objetos que comparten la misma área de trabajo (espacio de transacciones).  
  
-   Ha cambiado la clase de excepción. **Excepciones CDBException** se producen en las clases ODBC y **CDaoExceptions** en las clases DAO.  
  
-   `RFX_Date` usa `CTime` y **TIMESTAMP_STRUCT** objetos mientras **DFX_Date** utiliza `COleDateTime`. El `COleDateTime` es casi idéntica a `CTime`, pero se basa en una OLE de 8 bytes **fecha** en lugar de 4 bytes `time_t` por lo que puede almacenar una gama mucho más grande de datos.  
  
    > [!NOTE]
    >  DAO (`CDaoRecordset`) las instantáneas son de solo lectura mientras ODBC (`CRecordset`) pueden ser instantáneas actualizables según el controlador y el uso de la biblioteca de cursores ODBC. Si usas la biblioteca de cursores, `CRecordset` instantáneas son actualizables. Si usa cualquiera de los controladores de Microsoft de 3.0 de módulo de controlador de escritorio sin la biblioteca de cursores ODBC, el `CRecordset` instantáneas son de solo lectura. Si está utilizando otro controlador, compruebe la documentación del controlador para ver si las instantáneas (**STATIC_CURSORS**) son de solo lectura.  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

