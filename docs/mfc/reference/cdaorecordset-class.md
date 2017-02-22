---
title: "CDaoRecordset Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDaoRecordset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoRecordset (clase)"
  - "registros, CDaoRecordSet"
  - "conjuntos de registros, tipos"
ms.assetid: 2322067f-1027-4662-a5d7-aa2fc7488630
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CDaoRecordset Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa un conjunto de registros seleccionados de un origen de datos.  
  
## Sintaxis  
  
```  
  
class CDaoRecordset : public CObject  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoRecordset::CDaoRecordset](../Topic/CDaoRecordset::CDaoRecordset.md)|Crea un objeto `CDaoRecordset`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoRecordset::AddNew](../Topic/CDaoRecordset::AddNew.md)|Se prepara para agregar un nuevo registro.  Llamada [Actualizar](../Topic/CDaoRecordset::Update.md) para completar la suma.|  
|[CDaoRecordset::CanAppend](../Topic/CDaoRecordset::CanAppend.md)|Devuelve cero si los nuevos registros se pueden agregar al conjunto de registros mediante la función miembro de [AddNew](../Topic/CDaoRecordset::AddNew.md) .|  
|[CDaoRecordset::CanBookmark](../Topic/CDaoRecordset::CanBookmark.md)|Devuelve cero si el conjunto de registros admite marcadores.|  
|[CDaoRecordset::CancelUpdate](../Topic/CDaoRecordset::CancelUpdate.md)|Cancela cualquier actualización pendiente debido a una operación de [Editar](../Topic/CDaoRecordset::Edit.md) o de [AddNew](../Topic/CDaoRecordset::AddNew.md) .|  
|[CDaoRecordset::CanRestart](../Topic/CDaoRecordset::CanRestart.md)|Devuelve cero si [Requery](../Topic/CDaoRecordset::Requery.md) se puede llamar a para ejecutar la consulta de conjunto de registros de nuevo.|  
|[CDaoRecordset::CanScroll](../Topic/CDaoRecordset::CanScroll.md)|Devuelve cero si puede desplazarse por los registros.|  
|[CDaoRecordset::CanTransact](../Topic/CDaoRecordset::CanTransact.md)|Devuelve cero si el origen de datos admite transacciones.|  
|[CDaoRecordset::CanUpdate](../Topic/CDaoRecordset::CanUpdate.md)|Devuelve cero si el conjunto de registros se puede actualizar \(puede agregar, actualizar, o eliminar registros\).|  
|[CDaoRecordset::Close](../Topic/CDaoRecordset::Close.md)|Cierre el conjunto de registros.|  
|[CDaoRecordset::Delete](../Topic/CDaoRecordset::Delete.md)|Elimina el registro actual del conjunto de registros.  Debe explícitamente desplazarse a otro registro después de la eliminación.|  
|[CDaoRecordset::DoFieldExchange](../Topic/CDaoRecordset::DoFieldExchange.md)|Denominado para intercambiar los datos \(en ambas direcciones\) entre los miembros de datos de campo de conjunto de registros y el registro correspondiente en el origen de datos.  Intercambio de campos del registro de DAO de instrumenta \(DFX\).|  
|[CDaoRecordset::Edit](../Topic/CDaoRecordset::Edit.md)|Se prepara para los cambios del registro actual.  Llamada **Actualizar** para finalizar la edición.|  
|[CDaoRecordset::FillCache](../Topic/CDaoRecordset::FillCache.md)|Rellena la totalidad o una parte caché local para un objeto de conjunto de registros que contenga datos de un origen de datos ODBC.|  
|[CDaoRecordset::Find](../Topic/CDaoRecordset::Find.md)|Busque la primera, siguiente, anterior, o a la última ubicación de una cadena concreta en un conjunto de registros de dynaset\- tipo que cumpla los criterios especificados y la crea que registra el registro actual.|  
|[CDaoRecordset::FindFirst](../Topic/CDaoRecordset::FindFirst.md)|Buscar el primer registro en un conjunto de registros de dynaset\- tipo o de instantánea\- tipo que cumpla los criterios especificados y hace que registra el registro actual.|  
|[CDaoRecordset::FindLast](../Topic/CDaoRecordset::FindLast.md)|Busque el último registro en un conjunto de registros de dynaset\- tipo o de instantánea\- tipo que cumpla los criterios especificados y hace que registra el registro actual.|  
|[CDaoRecordset::FindNext](../Topic/CDaoRecordset::FindNext.md)|Busque el registro siguiente en un conjunto de registros de dynaset\- tipo o de instantánea\- tipo que cumpla los criterios especificados y hace que registra el registro actual.|  
|[CDaoRecordset::FindPrev](../Topic/CDaoRecordset::FindPrev.md)|Busque el registro anterior en un conjunto de registros de dynaset\- tipo o de instantánea\- tipo que cumpla los criterios especificados y hace que registra el registro actual.|  
|[CDaoRecordset::GetAbsolutePosition](../Topic/CDaoRecordset::GetAbsolutePosition.md)|Devuelve el número de registro del registro actual de un objeto de conjunto de registros.|  
|[CDaoRecordset::GetBookmark](../Topic/CDaoRecordset::GetBookmark.md)|Devuelve un valor que representa el marcador en un registro.|  
|[CDaoRecordset::GetCacheSize](../Topic/CDaoRecordset::GetCacheSize.md)|Devuelve un valor que especifica el número de registros de un conjunto de registros de dynaset\- tipo que contiene los datos localmente que se va a almacenar en memoria caché de un origen de datos ODBC.|  
|[CDaoRecordset::GetCacheStart](../Topic/CDaoRecordset::GetCacheStart.md)|Devuelve un valor que especifica el marcador del primer registro del conjunto de registros que se almacene en memoria caché.|  
|[CDaoRecordset::GetCurrentIndex](../Topic/CDaoRecordset::GetCurrentIndex.md)|Devuelve `CString` que contiene el nombre del índice utilizado recientemente en un indizado, tabla\- tipo `CDaoRecordset`.|  
|[CDaoRecordset::GetDateCreated](../Topic/CDaoRecordset::GetDateCreated.md)|Devuelve la fecha y hora en que la tabla base que era la base de un objeto de `CDaoRecordset` se creó|  
|[CDaoRecordset::GetDateLastUpdated](../Topic/CDaoRecordset::GetDateLastUpdated.md)|Devuelve la fecha y hora de cambio realizado más reciente en el diseño de una tabla base subyacente de un objeto de `CDaoRecordset` .|  
|[CDaoRecordset::GetDefaultDBName](../Topic/CDaoRecordset::GetDefaultDBName.md)|Devuelve el nombre del origen de datos predeterminado.|  
|[CDaoRecordset::GetDefaultSQL](../Topic/CDaoRecordset::GetDefaultSQL.md)|Denominado para obtener la cadena SQL predeterminada para ejecutarse.|  
|[CDaoRecordset::GetEditMode](../Topic/CDaoRecordset::GetEditMode.md)|Devuelve un valor que indica el estado de edición del registro actual.|  
|[CDaoRecordset::GetFieldCount](../Topic/CDaoRecordset::GetFieldCount.md)|Devuelve un valor que representa el número de campos en un conjunto de registros.|  
|[CDaoRecordset::GetFieldInfo](../Topic/CDaoRecordset::GetFieldInfo.md)|Devuelve los tipos de información concreta sobre los campos en el conjunto de registros.|  
|[CDaoRecordset::GetFieldValue](../Topic/CDaoRecordset::GetFieldValue.md)|Devuelve el valor de un campo de un conjunto de registros.|  
|[CDaoRecordset::GetIndexCount](../Topic/CDaoRecordset::GetIndexCount.md)|Recupera el número de índices en una tabla subyacente de un conjunto de registros.|  
|[CDaoRecordset::GetIndexInfo](../Topic/CDaoRecordset::GetIndexInfo.md)|Devuelve a distintos tipos de información sobre un índice.|  
|[CDaoRecordset::GetLastModifiedBookmark](../Topic/CDaoRecordset::GetLastModifiedBookmark.md)|Utilizado para determinar el registro recientemente agregado o actualizado.|  
|[CDaoRecordset::GetLockingMode](../Topic/CDaoRecordset::GetLockingMode.md)|Devuelve un valor que indica el tipo de bloqueo que esté en efecto durante la edición.|  
|[CDaoRecordset::GetName](../Topic/CDaoRecordset::GetName.md)|Devuelve `CString` que contiene el nombre del conjunto de registros.|  
|[CDaoRecordset::GetParamValue](../Topic/CDaoRecordset::GetParamValue.md)|Recupera el valor actual del parámetro especificado almacenado en el objeto subyacente de DAOParameter.|  
|[CDaoRecordset::GetPercentPosition](../Topic/CDaoRecordset::GetPercentPosition.md)|Devuelve la posición del registro actual como porcentaje del número de registros total.|  
|[CDaoRecordset::GetRecordCount](../Topic/CDaoRecordset::GetRecordCount.md)|Devuelve el número de registros obtenidos en un objeto de conjunto de registros.|  
|[CDaoRecordset::GetSQL](../Topic/CDaoRecordset::GetSQL.md)|Obtiene la cadena SQL utilizada para seleccionar registros del conjunto de registros.|  
|[CDaoRecordset::GetType](../Topic/CDaoRecordset::GetType.md)|Denominado para determinar el tipo de un conjunto de registros: tabla\-tipo, dynaset\-tipo, o instantánea\-tipo.|  
|[CDaoRecordset::GetValidationRule](../Topic/CDaoRecordset::GetValidationRule.md)|Devuelve `CString` que contiene el valor que valida los datos a medida que se escribe en un campo.|  
|[CDaoRecordset::GetValidationText](../Topic/CDaoRecordset::GetValidationText.md)|Recupera el texto que se muestra cuando una regla de validación no se cumple.|  
|[CDaoRecordset::IsBOF](../Topic/CDaoRecordset::IsBOF.md)|Devuelve cero si se ha colocado el conjunto de registros antes del primer registro.  No hay ningún registro actual.|  
|[CDaoRecordset::IsDeleted](../Topic/CDaoRecordset::IsDeleted.md)|Devuelve cero si colocan el conjunto de registros en un registro eliminado.|  
|[CDaoRecordset::IsEOF](../Topic/CDaoRecordset::IsEOF.md)|Devuelve cero si se ha colocado el conjunto de registros después del último registro.  No hay ningún registro actual.|  
|[CDaoRecordset::IsFieldDirty](../Topic/CDaoRecordset::IsFieldDirty.md)|Devuelve cero si el campo especificado en el registro actual se ha cambiado.|  
|[CDaoRecordset::IsFieldNull](../Topic/CDaoRecordset::IsFieldNull.md)|Devuelve cero si el campo especificado en el registro actual es Null \(no tener ningún valor\).|  
|[CDaoRecordset::IsFieldNullable](../Topic/CDaoRecordset::IsFieldNullable.md)|Devuelve cero si el campo especificado en el registro actual se puede establecer en Null \(no tener ningún valor\).|  
|[CDaoRecordset::IsOpen](../Topic/CDaoRecordset::IsOpen.md)|Devuelve cero si [Abrir](../Topic/CDaoRecordset::Open.md) se ha llamado previamente.|  
|[CDaoRecordset::Move](../Topic/CDaoRecordset::Move.md)|Coloca el conjunto de registros en un número de registros especificado del registro actual en cualquier dirección.|  
|[CDaoRecordset::MoveFirst](../Topic/CDaoRecordset::MoveFirst.md)|Coloca el registro actual respecto al primer registro del conjunto de registros.|  
|[CDaoRecordset::MoveLast](../Topic/CDaoRecordset::MoveLast.md)|Coloca el registro actual en el último registro en el conjunto de registros.|  
|[CDaoRecordset::MoveNext](../Topic/CDaoRecordset::MoveNext.md)|Coloca el registro actual en el registro siguiente en el conjunto de registros.|  
|[CDaoRecordset::MovePrev](../Topic/CDaoRecordset::MovePrev.md)|Coloca el registro actual en el registro anterior en el conjunto de registros.|  
|[CDaoRecordset::Open](../Topic/CDaoRecordset::Open.md)|Crea un nuevo conjunto de registros de una tabla, un conjunto, o de una instantánea.|  
|[CDaoRecordset::Requery](../Topic/CDaoRecordset::Requery.md)|Ejecuta la consulta de conjunto de registros de nuevo para actualizar los registros seleccionados.|  
|[CDaoRecordset::Seek](../Topic/CDaoRecordset::Seek.md)|Busque el registro en un objeto de conjunto de registros indizado de tabla\- tipo que cumpla los criterios especificados para el índice actual y hace que registra el registro actual.|  
|[CDaoRecordset::SetAbsolutePosition](../Topic/CDaoRecordset::SetAbsolutePosition.md)|Establece el número de registro del registro actual de un objeto de conjunto de registros.|  
|[CDaoRecordset::SetBookmark](../Topic/CDaoRecordset::SetBookmark.md)|Coloca el conjunto de registros en un registro que contiene el marcador especificado.|  
|[CDaoRecordset::SetCacheSize](../Topic/CDaoRecordset::SetCacheSize.md)|Establece un valor que especifica el número de registros de un conjunto de registros de dynaset\- tipo que contiene los datos localmente que se va a almacenar en memoria caché de un origen de datos ODBC.|  
|[CDaoRecordset::SetCacheStart](../Topic/CDaoRecordset::SetCacheStart.md)|Establece un valor que especifica el marcador del primer registro del conjunto de registros que se almacene en memoria caché.|  
|[CDaoRecordset::SetCurrentIndex](../Topic/CDaoRecordset::SetCurrentIndex.md)|Denominado para establecer un índice en un conjunto de registros de tabla\- tipo.|  
|[CDaoRecordset::SetFieldDirty](../Topic/CDaoRecordset::SetFieldDirty.md)|Marca el campo especificado en el registro actual como cambiado.|  
|[CDaoRecordset::SetFieldNull](../Topic/CDaoRecordset::SetFieldNull.md)|Establece el valor del campo especificado en el registro actual en Null \(no tener ningún valor\).|  
|[CDaoRecordset::SetFieldValue](../Topic/CDaoRecordset::SetFieldValue.md)|Establece el valor de un campo de un conjunto de registros.|  
|[CDaoRecordset::SetFieldValueNull](../Topic/CDaoRecordset::SetFieldValueNull.md)|Establece el valor de un campo de un conjunto de registros en Null.  \(no tener ningún valor\).|  
|[CDaoRecordset::SetLockingMode](../Topic/CDaoRecordset::SetLockingMode.md)|Establece un valor que indica el tipo de bloqueo para ejecutar durante la edición.|  
|[CDaoRecordset::SetParamValue](../Topic/CDaoRecordset::SetParamValue.md)|Establece el valor actual del parámetro especificado almacenado en el objeto subyacente de DAOParameter|  
|[CDaoRecordset::SetParamValueNull](../Topic/CDaoRecordset::SetParamValueNull.md)|Establece el valor actual del parámetro especificado en Null \(no tener ningún valor\).|  
|[CDaoRecordset::SetPercentPosition](../Topic/CDaoRecordset::SetPercentPosition.md)|Establece la posición del registro actual en una ubicación correspondiente a un porcentaje del número total de registros de un conjunto de registros.|  
|[CDaoRecordset::Update](../Topic/CDaoRecordset::Update.md)|Completa una operación de `AddNew` o de **Editar** guardar nuevos o editar datos en el origen de datos.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoRecordset::m\_bCheckCacheForDirtyFields](../Topic/CDaoRecordset::m_bCheckCacheForDirtyFields.md)|Contiene una marca que indica si los campos automáticamente están marcados como cambiado.|  
|[CDaoRecordset::m\_nFields](../Topic/CDaoRecordset::m_nFields.md)|Contiene el número de miembros de datos de campo en la clase de conjunto de registros y el número de columnas seleccionadas por el conjunto de registros del origen de datos.|  
|[CDaoRecordset::m\_nParams](../Topic/CDaoRecordset::m_nParams.md)|Contiene el número de miembros de datos de parámetro en la clase de conjunto de registros \(el número de parámetros pasados con la consulta de conjunto de registros|  
|[CDaoRecordset::m\_pDAORecordset](../Topic/CDaoRecordset::m_pDAORecordset.md)|Un puntero a la interfaz de DAO al objeto de conjunto de registros.|  
|[CDaoRecordset::m\_pDatabase](../Topic/CDaoRecordset::m_pDatabase.md)|Base de datos de origen para este conjunto de resultados.  Contiene un puntero a un objeto de [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) .|  
|[CDaoRecordset::m\_strFilter](../Topic/CDaoRecordset::m_strFilter.md)|Contiene una cadena utilizada para construir un extracto de SQL **WHERE** .|  
|[CDaoRecordset::m\_strSort](../Topic/CDaoRecordset::m_strSort.md)|Contiene una cadena utilizada para construir un extracto de SQL **ORDER BY** .|  
  
## Comentarios  
 Conocido como “conjuntos de registros”, los objetos de `CDaoRecordset` están disponibles en las tres formas siguientes:  
  
-   Los conjuntos de registros de Tabla\- tipo representa una tabla base que puede utilizar para examinar, para agregar, cambiar, o eliminar registros de una única tabla de base de datos.  
  
-   Los conjuntos de registros de Dynaset\- tipo son el resultado de una consulta que pueda tener registros actualizables.  Estos conjuntos de registros son un conjunto de registros que puede utilizar para examinar, para agregar, cambiar, o eliminar registros de una tabla o de tablas de base de datos subyacente.  Los conjuntos de registros de Dynaset\- tipo pueden contener campos de una o más tablas en una base de datos.  
  
-   Los conjuntos de registros de Instantánea\- tipo son una copia estática de un conjunto de registros que se puede utilizar para buscar datos o para generar informes.  Estos conjuntos de registros pueden contener campos de una o más tablas en una base de datos pero no pueden actualizarse.  
  
 Cada formulario de conjunto de registros representa un conjunto de registros corregidos cuando se abre el conjunto de registros.  Cuando se desplace a un registro en un conjunto de registros de tabla\- tipo o un conjunto de registros de dynaset\- tipo, refleja los cambios realizados en el registro después de que otros conjuntos de registros en la aplicación abre el conjunto de registros, por otros usuarios o.  \(El conjunto de registros de instantánea\- tipo de A no puede actualizarse.\) Puede utilizar `CDaoRecordset` directamente o derivar una clase específica de la aplicación de conjunto de registros `CDaoRecordset`.  Seguidamente puede:  
  
-   Desplácese por los registros.  
  
-   Establezca un índice y buscar rápidamente los registros utilizando [búsqueda](../Topic/CDaoRecordset::Seek.md) \(conjuntos de registros de tabla\- tipo sólo\).  
  
-   Busque los registros basándose en una comparación de cadenas: “\<”, “\<\=”, “\=”, “\>\=”, o “\>” \(conjuntos de registros de dynaset\- tipo y el instantánea\- tipo\).  
  
-   Actualizar registros y especifique un modo de bloqueo \(excepto los conjuntos de registros de instantánea\- tipo\).  
  
-   Filtre el conjunto de registros para restringir qué registros se seleccionan de los disponibles en el origen de datos.  
  
-   Ordenar el conjunto de registros.  
  
-   Parametrizar el conjunto de registros para personalizar la selección con información no conocida hasta el tiempo de ejecución.  
  
 Ordenar las fuentes de `CDaoRecordset` una interfaz similar a la de la clase `CRecordset`.  La diferencia principal es que la clase `CDaoRecordset` tiene acceso a datos a través de un Objeto de acceso a datos \(DAO\) basado en OLE.  Ordenar los métodos de `CRecordset` DBMS con \(ODBC\) y un controlador ODBC para ese DBMS.  
  
> [!NOTE]
>  Las clases de base de datos de DAO son distintas de las clases de base de datos MFC basadas en ODBC.  Todos los nombres de clase de base de datos de DAO tienen el prefijo “CDao”.  Todavía puede tener acceso a orígenes de datos ODBC con las clases DAO; las clases DAO suelen proporcionar capacidades máximas porque son específicas del motor de base de datos Microsoft Jet.  
  
 Puede utilizar `CDaoRecordset` directamente o derivar una clase de `CDaoRecordset`.  Para utilizar una clase de conjunto de registros en cualquier caso, abrir una base de datos y crear un objeto de conjunto de registros, pasando al constructor un puntero al objeto de `CDaoDatabase` .  También puede crear un objeto de `CDaoRecordset` y permite MFC crear un objeto temporal de `CDaoDatabase` automáticamente.  Llamar a continuación a la función miembro de [Abrir](../Topic/CDaoRecordset::Open.md) de conjunto de registros, que especifica si el objeto es un conjunto de registros de tabla\- tipo, un conjunto de registros de dynaset\- tipo, o un conjunto de registros de instantánea\- tipo.  La llamada **Open** selecciona los datos de la base de datos y recupera el primer registro.  
  
 Utilice las funciones y los miembros de datos de miembro de objeto desplazarse a través de los registros y operelos en.  Las operaciones disponibles dependen de si el objeto es un conjunto de registros de tabla\- tipo, un conjunto de registros de dynaset\- tipo, o un conjunto de registros de instantánea\- tipo y, si es actualizable o de sólo lectura — éste depende de la capacidad de la base de datos o el origen de datos de ODBC.  Para actualizar registros que hayan sido modificados o haber sido agregados desde la llamada de **Abrir** , llama a la función miembro de [Requery](../Topic/CDaoRecordset::Requery.md) del objeto.  Llame a la función miembro de **Cerrar** de objeto y destruya el objeto cuando acaba con él.  
  
 Intercambio de campos del registro de DAO de las aplicaciones de`CDaoRecordset` \(DFX\) para admitir la lectura y actualización de campos de registros entre los miembros tipo\- seguros de C\+\+ del `CDaoRecordset` o de `CDaoRecordset`\- clase derivada.  También puede implementar el enlace dinámico de columnas en una base de datos sin utilizar el mecanismo de DFX mediante [GetFieldValue](../Topic/CDaoRecordset::GetFieldValue.md) y [SetFieldValue](../Topic/CDaoRecordset::SetFieldValue.md).  
  
 Para obtener información relacionada, vea el tema “objeto de conjunto de registros” en DAO Help.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoRecordset`  
  
## Requisitos  
 **encabezado:** afxdao.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDaoTableDef Class](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoWorkspace Class](../../mfc/reference/cdaoworkspace-class.md)   
 [CDaoDatabase Class](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoQueryDef Class](../../mfc/reference/cdaoquerydef-class.md)