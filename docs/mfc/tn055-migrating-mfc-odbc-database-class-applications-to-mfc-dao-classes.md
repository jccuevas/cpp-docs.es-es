---
title: 'TN055: Migrar aplicaciones de clase de base de datos ODBC de MFC a clases DAO de MFC'
ms.date: 06/20/2018
f1_keywords:
- vc.mfc.odbc
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
ms.openlocfilehash: f8e0d8e50f05e86c35e0f8b7f324533bffea6f25
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487105"
---
# <a name="tn055-migrating-mfc-odbc-database-class-applications-to-mfc-dao-classes"></a>TN055: Migrar aplicaciones de clase de base de datos ODBC de MFC a clases DAO de MFC

> [!NOTE]
> El entorno de Visual C++ y los asistentes no admiten DAO (aunque las clases DAO están incluidas y puede seguir usándolos). Microsoft recomienda que utilice [plantillas OLE DB](../data/oledb/ole-db-templates.md) o [ODBC y MFC](../data/odbc/odbc-and-mfc.md) para los proyectos nuevos. Sólo se debe utilizar DAO mantener las aplicaciones existentes.

## <a name="overview"></a>Información general

En muchas situaciones puede ser deseable para migrar las aplicaciones que utilizan las clases de base de datos ODBC de MFC a clases de base de datos DAO de MFC. Esta nota técnica detallará la mayoría de las diferencias entre las clases DAO y ODBC de MFC. Teniendo en cuenta las diferencias, no debe ser demasiado difícil migrar aplicaciones desde las clases ODBC de las clases MFC si lo desea.

## <a name="why-migrate-from-odbc-to-dao"></a>¿Por qué migrar de ODBC a DAO

Hay una serie de razones por las que es posible que desea migrar aplicaciones desde las clases de base de datos ODBC a las clases de base de datos DAO, pero la decisión de no es necesariamente simple u obvio. Una cosa a tener en cuenta es que el motor de base de datos Microsoft Jet que se usa por DAO puede leer cualquier origen de datos ODBC para el que tiene un controlador ODBC. Puede ser más eficaz utilizar las clases de base de datos ODBC o llamar a ODBC directamente por sí mismo, pero el motor de base de datos Microsoft Jet puede leer los datos ODBC.

Los casos más sencillos que facilitan la decisión de ODBC o DAO. Por ejemplo, cuando sólo necesita acceso a datos en un formato que el motor Microsoft Jet puede leer directamente (formato de Access, formato de Excel etc.) es la opción obvia usar las clases de base de datos DAO.

Los casos más complejos se producen cuando los datos existen en un servidor o en una variedad de distintos servidores. En este caso, la decisión de utilizar las clases de base de datos ODBC o las clases de base de datos DAO es difícil. Si desea hacer cosas como combinaciones heterogéneas (combinación de datos de los servidores en varios formatos, como SQL Server y Oracle) y, después, el motor de base de datos Microsoft Jet llevará a cabo la combinación de que en lugar de obligarle a hacer el trabajo necesario si usa la base de datos ODBC Las clases u ODBC llamado directamente. Si usa un controlador ODBC que admite cursores del controlador, la mejor opción podría ser las clases de base de datos ODBC.

La opción puede ser complicada, por lo que es posible que desee escribir algún código de ejemplo para probar el rendimiento de diversos métodos según sus necesidades especiales. Esta nota técnica se da por supuesto que ha realizado la decisión de migrar de las clases de base de datos ODBC a las clases de base de datos DAO.

## <a name="similarities-between-odbc-database-classes-and-mfc-dao-database-classes"></a>Similitudes entre las clases de base de datos ODBC y las clases de base de datos DAO de MFC

El diseño original de las clases ODBC de MFC se basa en el modelo de objetos DAO que estuvo en uso en Microsoft Access y Microsoft Visual Basic. Esto significa que hay muchas características comunes de las clases ODBC y DAO de MFC, que no todos se mostrará en esta sección. En general, los modelos de programación son los mismos.

Para resaltar algunas similitudes:

- Las clases ODBC y DAO tienen objetos de base de datos que administrar mediante el sistema de administración de bases de datos (DBMS) subyacente.

- Ambos tienen objetos de conjunto de registros que representan un conjunto de resultados devueltos de ese DBMS.

- Los objetos de base de datos y el conjunto de registros DAO tengan miembros prácticamente idénticos a las clases ODBC.

- Con dos conjuntos de clases, el código para recuperar los datos es idéntico salvo algunos cambios de nombre de objeto y miembro. Se requiere cambios, pero normalmente el proceso es un cambio de nombre sencillo al cambiar de las clases ODBC a clases DAO.

Por ejemplo, en ambos modelos crear y abrir un objeto de base de datos, crear y abrir un objeto de conjunto de registros y desplazarse (mover) por los datos que realizar alguna operación es el procedimiento para recuperar los datos.

## <a name="differences-between-odbc-and-dao-mfc-classes"></a>Diferencias entre clases de MFC DAO y ODBC

Las clases DAO incluyen más objetos y un conjunto más completo de métodos, pero en esta sección solo se detallará las diferencias de funcionalidad y las clases similares.

Probablemente las diferencias entre las clases más obvias son los cambios de nombre de las clases similares y funciones globales. La siguiente lista muestra los cambios de nombre de los objetos, métodos y funciones globales asociadas con las clases de base de datos:

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
|`RFX_Date`<sup>1</sup>|`DFX_Date` (`COleDateTime`-según)|
|`RFX_Text`|`DFX_Text`|
|`RFX_Binary`|`DFX_Binary`|
|`RFX_LongBinary`|`DFX_LongBinary`|

<sup>1</sup> el `RFX_Date` función se basa en `CTime` y `TIMESTAMP_STRUCT`.

Los cambios más importantes a la funcionalidad que pueden afectar a la aplicación y requieren cambios de nombre más que un simple se enumeran a continuación.

- Las constantes y macros que se usa para especificar tipo de cosas como conjunto de registros abierto y conjunto de registros abierto opciones han cambiado.

   Con las clases ODBC de MFC necesarios para definir estas opciones mediante las macros o los tipos enumerados.

   Con las clases DAO, DAO proporciona la definición de estas opciones en un archivo de encabezado (DBDAOINT. (H). Por lo tanto el tipo de conjunto de registros es un miembro enumerado de `CRecordset`, pero con DAO es una constante en su lugar. Por ejemplo, usaría **instantánea** al especificar el tipo de `CRecordset` en ODBC, pero **DB_OPEN_SNAPSHOT** al especificar el tipo de `CDaoRecordset`.

- El tipo de conjunto de registros predeterminado para `CRecordset` es **instantánea** mientras que el tipo de conjunto de registros de forma predeterminada para `CDaoRecordset` es **dynaset** (consulte la nota a continuación para un problema adicional acerca de las instantáneas de clase ODBC).

- ODBC `CRecordset` clase tiene una opción para crear un tipo de conjunto de registros solo hacia delante. En el `CDaoRecordset` (clase), solo hacia delante no es un tipo de conjunto de registros, pero en su lugar una propiedad (u opción) de ciertos tipos de conjuntos de registros.

- Un conjunto de registros de solo anexión al abrir un `CRecordset` objeto significaba que los datos del conjunto de registros se podrían leer y anexar. Con `CDaoRecordset` de objeto, la opción de solo anexión literalmente significa que los datos del conjunto de registros solo se pueden anexar (y no de lectura).

- Las funciones miembro de transacción de las clases de ODBC son miembros de `CDatabase` y actuar en el nivel de base de datos. En las clases DAO, las funciones de miembro de la transacción son miembros de una clase de nivel superior (`CDaoWorkspace`) y, por tanto, puede afectar a varios `CDaoDatabase` objetos que comparten la misma área de trabajo (espacio de transacciones).

- La clase de excepción se ha cambiado. `CDBExceptions` se produce en las clases ODBC y `CDaoExceptions` en las clases DAO.

- `RFX_Date` usa `CTime` y `TIMESTAMP_STRUCT` objetos mientras `DFX_Date` usa `COleDateTime`. El `COleDateTime` es casi idéntico al `CTime`, pero se basa en una OLE de 8 bytes **fecha** en lugar de 4 bytes **time_t** por lo que puede almacenar una gama mucho más grande de datos.

   > [!NOTE]
   > DAO (`CDaoRecordset`) las instantáneas son de solo lectura mientras ODBC (`CRecordset`) las instantáneas se pueden actualizables según el controlador y el uso de la biblioteca de cursores ODBC. Si usa la biblioteca de cursores, `CRecordset` instantáneas son actualizables. Si usa cualquiera de los controladores de Microsoft desde el escritorio controlador Pack 3.0 sin la biblioteca de cursores ODBC, el `CRecordset` instantáneas son de solo lectura. Si está utilizando otro controlador, compruebe la documentación del controlador para ver si las instantáneas (`STATIC_CURSORS`) son de solo lectura.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
