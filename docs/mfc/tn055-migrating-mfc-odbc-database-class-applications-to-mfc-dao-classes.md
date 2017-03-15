---
title: "TN055: Migrar aplicaciones de clase de base de datos ODBC de MFC a clases DAO de MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.odbc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DAO [C++], migración"
  - "migrar aplicaciones de bases de datos"
  - "migrar aplicaciones de bases de datos ODBC"
  - "migración [C++], aplicaciones de base de datos ODBC"
  - "ODBC [C++], DAO"
  - "clases ODBC [C++], clases DAO"
  - "trasladar aplicaciones de bases de datos a DAO"
  - "trasladar aplicaciones de bases de datos ODBC a DAO"
  - "TN055"
ms.assetid: 0f858bd1-e168-4e2e-bcd1-8debd82856e4
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# TN055: Migrar aplicaciones de clase de base de datos ODBC de MFC a clases DAO de MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  A partir de Visual C\+\+ .NET, el entorno y los asistentes de Visual C\+\+ ya no admiten DAO \(aunque las clases DAO están incluidas y todavía puede utilizarlas\).  Microsoft recomienda utilizar [Plantillas OLE DB](../data/oledb/ole-db-templates.md) o [ODBC y MFC](../data/odbc/odbc-and-mfc.md) para nuevos proyectos.  Sólo debería utilizar DAO para mantener las aplicaciones existentes.  
  
 **Información general**  
  
 En muchas situaciones puede ser deseable migrar las aplicaciones que utilizan las clases de base de datos ODBC de MFC a las clases de base de datos de DAO de MFC.  Esta nota técnica detallará la mayor parte de las diferencias entre las clases ODBC y DAO de MFC.  Con las diferencias presente, no debe ser demasiado difícil migrar aplicaciones de las clases ODBC a las clases MFC si lo desea.  
  
 **¿Por qué migrar de ODBC a DAO?**  
  
 Hay varias razones por las que podría desear migrar aplicaciones de las clases de base de datos ODBC a las clases de base de datos de DAO, pero la decisión no es necesariamente simple u obvia.  Un aspecto que tener en cuenta es que el motor de base de datos Microsoft Jet que usa DAO puede leer cualquier origen de datos ODBC para el que se tenga un controlador ODBC.  Puede ser más eficaz utilizar las clases de base de datos ODBC o llamar a ODBC directamente el mismo, pero el motor de base de datos Microsoft Jet puede leer los datos de ODBC.  
  
 Algunos casos sencillos que toman la decisión de ODBC\/DAO fácil.  Formato por ejemplo, si solo necesita acceso a los datos en un formato que el motor de Microsoft Jet pueda leer directamente \(formato de Access, de Excel, etc.\) a la opción obvia es utilizar las clases de base de datos de DAO.  
  
 Casos más complejos surgen cuando los datos existe en un servidor o en distintos servidores.  En este caso, la decisión de utilizar las clases de base de datos ODBC o las clases de base de datos de DAO es difícil.  Si desea realizar tareas como heterogéneo combinaciones \(los datos de la unión de los servidores en varios formatos como SQL Server y Oracle\), el motor de base de datos Microsoft Jet realiza la combinación para se en lugar de obligarle para hacer el trabajo necesario si utilizó las clases de base de datos ODBC o denominado ODBC directamente.  Si utiliza un controlador ODBC que sea compatible con los cursores de controlador, la mejor opción podría ser clases de base de datos ODBC.  
  
 La opción puede ser complicada, por lo que puede resultar conveniente para escribir código muestra para probar el rendimiento de los distintos métodos con el necesidades especiales.  Esta nota técnica supone que ha tomado la decisión para migrar de las clases de base de datos ODBC a las clases de base de datos de DAO.  
  
 **Clases de base de datos ODBC de entre las similitudes y las clases de base de datos DAO de MFC**  
  
 El diseño original de las clases ODBC de MFC se basaba en el modelo de objetos DAO que ha sido en uso en Microsoft Access y Microsoft Visual Basic.  Esto significa que hay muchas características comunes de las clases ODBC y DAO MFC, que todos no aparecerán en esta sección.  Los modelos de programación normalmente son iguales.  
  
 Para resaltar algunas similitudes:  
  
-   Las clases ODBC y DAO tienen objetos de base de datos que administren mediante el sistema de administración de base de datos subyacente \(DBMS\).  
  
-   Ambos tienen objetos de conjunto de registros que representan un conjunto de resultados devueltos de ese DBMS.  
  
-   La base de datos y los objetos de conjunto de registros DAO tienen miembros casi idénticos a las clases ODBC.  
  
-   Con ambos conjuntos de clases, el código para recuperar datos es idéntico a excepción de algunos cambios de objeto y de nombre de miembro.  Los cambios se necesarios, pero el proceso es normalmente un cambio de nombre directo al cambiar de las clases ODBC a las clases DAO.  
  
 Por ejemplo, en ambos modelos el procedimiento para recuperar datos es crear y abrir un objeto de base de datos, crear y abrir un objeto de conjunto de registros, y navegar \(mover\) sin embargo los datos que realicen alguna operación.  
  
 **Diferencias Entre ODBC y clases MFC de DAO**  
  
 Las clases DAO incluyen más objetos y un conjunto más completo de métodos, pero esta sección detallará solo las diferencias en clases y funciones similares.  
  
 Las diferencias más obvias entre clases son probablemente los cambios de nombre para las clases similares y funciones globales.  La lista siguiente muestra los cambios de nombre de los objetos, los métodos y las funciones globales asociados a las clases de base de datos:  
  
|Clase o función|Equivalentes de las clases DAO de MFC|  
|---------------------|-------------------------------------------|  
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
|**RFX\_Date \***|**DFX\_Date** \(`COleDateTime`\(función\)|  
|`RFX_Text`|`DFX_Text`|  
|`RFX_Binary`|`DFX_Binary`|  
|`RFX_LongBinary`|`DFX_LongBinary`|  
  
 \* La función de El `RFX_Date` se basa en `CTime` y **TIMESTAMP\_STRUCT**.  
  
 Los cambios principales a la funcionalidad que puede afectar a la aplicación y requiere más de cambios de nombre simple se enumeran.  
  
-   Las constantes y macros utilizadas para especificar elementos como el conjunto de registros abra tipo y se han cambiado las opciones abierto de conjunto de registros.  
  
     Con las clases ODBC MFC para definir estas opciones mediante macros o tipos enumerados.  
  
     Con las clases DAO, DAO proporciona la definición de estas opciones en un archivo de encabezado \(DBDAOINT.H\).  Para el tipo de conjunto de registros es miembro enumerado de `CRecordset`, pero con DAO es una constante en su lugar.  Por ejemplo utilizaría **instantánea** al especificar el tipo de `CRecordset` en ODBC pero **DB\_OPEN\_SNAPSHOT** al especificar el tipo de `CDaoRecordset`.  
  
-   El conjunto de registros predeterminado con tipo para `CRecordset` es **instantánea** mientras el tipo predeterminado de conjunto de registros para `CDaoRecordset` es **dynaset** \(vea la nota siguiente para un problema adicional sobre instantáneas de la clase de ODBC\).  
  
-   La clase de ODBC `CRecordset` tiene una opción de crear un tipo frontal \- sólo de conjunto de registros.  En la clase de `CDaoRecordset` , adelantada \- solo es un no tipo de conjunto de registros, sino una propiedad \(o la opción\) de determinados tipos de conjuntos de registros.  
  
-   Un conjunto de registros append \- sólo al abrir un objeto de `CRecordset` significaba que los datos del conjunto de registros pueden leer y ser anexados.  Con el objeto de `CDaoRecordset` , la opción de anexar \- sólo significa literalmente que los datos del conjunto de registros pueden ser anexados sólo \(y no lectura\).  
  
-   Las funciones miembro de transacción de las clases ODBC son miembros de `CDatabase` y actuar en el nivel de base de datos.  En las clases DAO, las funciones miembro de transacción son miembros de una clase de alto nivel \(`CDaoWorkspace`\) y pueden influir para varios objetos de `CDaoDatabase` que comparten la misma área de trabajo \(espacio de la transacción\).  
  
-   Se ha cambiado la clase de excepción.  **CDBExceptions** se produce en las clases y **CDaoExceptions** ODBC en las clases DAO.  
  
-   `RFX_Date` utiliza `CTime` y los objetos de **TIMESTAMP\_STRUCT** mientras **DFX\_Date** utiliza `COleDateTime`.  `COleDateTime` es casi idéntico a `CTime`, pero se basa en 8 byte **date** OLE en lugar de 4 byte `time_t` así que puede contener un rango de datos mucho mayor.  
  
    > [!NOTE]
    >  Instantáneas de DAO \(`CDaoRecordset`\) son de sólo lectura mientras instantáneas de ODBC \(`CRecordset`\) pueden ser actualizables dependiendo del controlador y el uso de la biblioteca de cursores ODBC.  Si utiliza la biblioteca de cursores, las instantáneas de `CRecordset` son actualizables.  Si utiliza controladores cualquiera de Microsoft de controlador de escritorio empaquetan 3,0 sin la biblioteca de cursores ODBC, las instantáneas de `CRecordset` son de solo lectura.  Si utiliza otro controlador, compruebe la documentación del controlador para ver si las instantáneas \(**STATIC\_CURSORS**\) son de solo lectura.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)