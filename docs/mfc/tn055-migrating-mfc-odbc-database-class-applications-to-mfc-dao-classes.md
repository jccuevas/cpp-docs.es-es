---
title: 'TN055: Migrar aplicaciones de clase de base de datos ODBC de MFC a clases DAO de MFC'
ms.date: 09/17/2019
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
ms.openlocfilehash: 744e1c71476ccfbe6ea8f8359dcdb9a29efc995e
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74305363"
---
# <a name="tn055-migrating-mfc-odbc-database-class-applications-to-mfc-dao-classes"></a>TN055: Migrar aplicaciones de clase de base de datos ODBC de MFC a clases DAO de MFC

> [!NOTE]
> DAO se utiliza con bases de datos de Access y se admite a través de Office 2013. DAO 3,6 es la versión final y se considera obsoleta. Los asistentes C++ y el entorno visual no admiten DAO (aunque las clases DAO están incluidas y todavía se pueden utilizar). Microsoft recomienda que use [plantillas de OLE DB](../data/oledb/ole-db-templates.md) u [ODBC y MFC](../data/odbc/odbc-and-mfc.md) para proyectos nuevos. Solo se debe utilizar DAO en el mantenimiento de las aplicaciones existentes.

## <a name="overview"></a>Información general

En muchas situaciones, puede ser conveniente migrar las aplicaciones que usan las clases de base de datos ODBC de MFC a las clases de base de datos DAO de MFC. En esta nota técnica se detallarán la mayoría de las diferencias entre las clases ODBC y DAO de MFC. Teniendo en cuenta las diferencias, no debería ser demasiado difícil migrar las aplicaciones de las clases ODBC a las clases MFC si lo desea.

## <a name="why-migrate-from-odbc-to-dao"></a>Por qué migrar de ODBC a DAO

Hay una serie de motivos por los que es posible que desee migrar aplicaciones de las clases de base de datos ODBC a las clases de base de datos DAO, pero la decisión no es necesariamente simple o obvia. Es importante tener en cuenta que el motor de base de datos de Microsoft Jet que usa DAO puede leer cualquier origen de datos ODBC para el que tenga un controlador ODBC. Puede ser más eficaz usar las clases de base de datos ODBC o llamar a ODBC directamente, pero el motor de base de datos de Microsoft Jet puede leer datos ODBC.

Algunos casos sencillos facilitan la decisión de ODBC/DAO. Por ejemplo, si solo necesita tener acceso a los datos en un formato que el motor de Microsoft Jet pueda leer directamente (formato de acceso, formato de Excel, etc.), la opción obvia es usar las clases de base de datos DAO.

Se producen casos más complejos cuando los datos existen en un servidor o en varios servidores diferentes. En este caso, la decisión de utilizar las clases de base de datos ODBC o las clases de base de datos DAO es una tarea difícil. Si desea hacer cosas como combinaciones heterogéneas (combinar datos de servidores en varios formatos como SQL Server y Oracle), el motor de base de datos de Microsoft Jet realizará la combinación en lugar de obligarle a realizar el trabajo necesario si ha utilizado la base de datos ODBC. Clases o llamadas ODBC directamente. Si usa un controlador ODBC que admita cursores de controlador, la mejor opción podría ser las clases de base de datos ODBC.

La elección puede ser complicada, por lo que es posible que desee escribir código de ejemplo para probar el rendimiento de varios métodos según sus necesidades especiales. En esta nota técnica se supone que ha tomado la decisión de migrar de las clases de base de datos ODBC a las clases de base de datos DAO.

## <a name="similarities-between-odbc-database-classes-and-mfc-dao-database-classes"></a>Similitudes entre las clases de base de datos ODBC y las clases de base de datos DAO de MFC

El diseño original de las clases ODBC de MFC se basó en el modelo de objetos de DAO que se ha utilizado en Microsoft Access y Microsoft Visual Basic. Esto significa que hay muchas características comunes de las clases MFC de ODBC y DAO, que no se mostrarán en esta sección. En general, los modelos de programación son los mismos.

Para resaltar algunas similitudes:

- Las clases ODBC y DAO tienen objetos de base de datos que administran mediante el sistema de administración de bases de datos (DBMS) subyacente.

- Ambos tienen objetos de conjunto de registros que representan un conjunto de resultados devueltos de ese DBMS.

- Los objetos de base de datos y de conjunto de registros DAO tienen miembros casi idénticos a los de las clases ODBC.

- Con ambos conjuntos de clases, el código para recuperar datos es idéntico, salvo en el caso de algunos cambios en el nombre de los objetos y miembros. Los cambios serán necesarios, pero normalmente el proceso es un cambio de nombre sencillo al cambiar de las clases ODBC a clases DAO.

Por ejemplo, en ambos modelos el procedimiento para recuperar datos es crear y abrir un objeto de base de datos, crear y abrir un objeto de conjunto de registros y navegar (moverse) a través de los datos que realizan alguna operación.

## <a name="differences-between-odbc-and-dao-mfc-classes"></a>Diferencias entre las clases MFC de ODBC y DAO

Las clases DAO incluyen más objetos y un conjunto de métodos más completo, pero en esta sección solo se detallan las diferencias de clases y funcionalidades similares.

Probablemente, las diferencias más obvias entre las clases son los cambios de nombre para las clases y funciones globales similares. En la lista siguiente se muestran los cambios de nombre de los objetos, métodos y funciones globales asociados a las clases de base de datos:

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
|`RFX_Date`<sup>1</sup>|`DFX_Date` (basado en`COleDateTime`)|
|`RFX_Text`|`DFX_Text`|
|`RFX_Binary`|`DFX_Binary`|
|`RFX_LongBinary`|`DFX_LongBinary`|

<sup>1</sup> la función `RFX_Date` se basa en `CTime` y `TIMESTAMP_STRUCT`.

A continuación se enumeran los cambios importantes en la funcionalidad que pueden afectar a la aplicación y que requieren más de cambios de nombre sencillos.

- Se han cambiado las constantes y macros utilizadas para especificar elementos como las opciones Open Recordset y Open Recordset.

   Con las clases ODBC que MFC necesitaba para definir estas opciones mediante macros o tipos enumerados.

   Con las clases DAO, DAO proporciona la definición de estas opciones en un archivo de encabezado (DBDAOINT. H). Por lo tanto, el tipo de conjunto de registros es un miembro enumerado de `CRecordset`, pero con DAO es una constante en su lugar. Por ejemplo, debería utilizar la **instantánea** al especificar el tipo de `CRecordset` en ODBC, pero **DB_OPEN_SNAPSHOT** al especificar el tipo de `CDaoRecordset`.

- El tipo de conjunto de registros predeterminado para `CRecordset` es **Snapshot** mientras que el tipo de conjunto de registros predeterminado para `CDaoRecordset` es **Dynaset** (vea la nota siguiente para ver un problema adicional sobre las instantáneas de clase ODBC).

- La clase `CRecordset` ODBC tiene una opción para crear un tipo de conjunto de registros de solo avance. En la clase `CDaoRecordset`, solo avance no es un tipo de conjunto de registros, sino una propiedad (u opción) de ciertos tipos de conjuntos de registros.

- Un conjunto de registros de solo anexar al abrir un `CRecordset` objeto significaba que los datos del conjunto de registros se podían leer y anexar. Con `CDaoRecordset` objeto, la opción solo anexar significa literalmente que los datos del conjunto de registros solo se pueden anexar (y no leer).

- Las funciones miembro de transacción de las clases ODBC son miembros de `CDatabase` y actúan en el nivel de base de datos. En las clases DAO, las funciones miembro de transacción son miembros de una clase de nivel superior (`CDaoWorkspace`) y, por lo tanto, pueden afectar a varios objetos `CDaoDatabase` que comparten la misma área de trabajo (espacio de transacciones).

- Se ha cambiado la clase de excepción. `CDBExceptions` se producen en las clases y `CDaoExceptions` de ODBC en las clases DAO.

- `RFX_Date` usa objetos `CTime` y `TIMESTAMP_STRUCT` mientras `DFX_Date` utiliza `COleDateTime`. El `COleDateTime` es casi idéntico a `CTime`, pero se basa en una **fecha** OLE de 8 bytes en lugar de una **time_t** de 4 bytes, por lo que puede contener un rango de datos mucho mayor.

   > [!NOTE]
   > Las instantáneas DAO (`CDaoRecordset`) son de solo lectura, mientras que las instantáneas ODBC (`CRecordset`) pueden ser actualizables según el controlador y el uso de la biblioteca de cursores ODBC. Si usa la biblioteca de cursores, `CRecordset` instantáneas son actualizables. Si usa cualquiera de los controladores de Microsoft de Desktop driver Pack 3,0 sin la biblioteca de cursores ODBC, las instantáneas de `CRecordset` son de solo lectura. Si usa otro controlador, consulte la documentación del controlador para ver si las instantáneas (`STATIC_CURSORS`) son de solo lectura.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
