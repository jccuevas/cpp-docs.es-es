---
title: "CDatabase Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDatabase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDatabase (clase)"
  - "clases de base de datos [C++], ODBC"
  - "conexiones de bases de datos [C++], CDatabase (clase)"
  - "MFC [C++], ODBC"
  - "ODBC [C++], CDatabase (clase)"
  - "ODBC database class"
ms.assetid: bd0de70a-e3c3-4441-bcaa-bbf434426ca8
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CDatabase Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una conexión a un origen de datos, con el que puede trabajar con el origen de datos.  
  
## Sintaxis  
  
```  
  
class CDatabase : public CObject  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDatabase::CDatabase](../Topic/CDatabase::CDatabase.md)|Crea un objeto `CDatabase`.  Debe inicializar el objeto llamando a `OpenEx` o **Abrir**.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDatabase::BeginTrans](../Topic/CDatabase::BeginTrans.md)|Inicia una transacción “” — una serie de llamadas reversibles a las funciones de `AddNew`, el miembro de **Editar**, de **Eliminar**, y de **Update** de la clase `CRecordset` \)del origen de datos conectado.  El origen de datos debe admitir las transacciones para que **BeginTrans** con ningún efecto.|  
|[CDatabase::BindParameters](../Topic/CDatabase::BindParameters.md)|Permite a los parámetros de enlace antes de llamar a `CDatabase::ExecuteSQL`.|  
|[CDatabase::Cancel](../Topic/CDatabase::Cancel.md)|Cancela una operación asincrónica o un proceso de segundo subproceso.|  
|[CDatabase::CanTransact](../Topic/CDatabase::CanTransact.md)|Devuelve cero si el origen de datos admite transacciones.|  
|[CDatabase::CanUpdate](../Topic/CDatabase::CanUpdate.md)|Devuelve cero si el objeto de `CDatabase` es actualizable \(no de sólo lectura\).|  
|[CDatabase::Close](../Topic/CDatabase::Close.md)|cierra la conexión a un origen de datos.|  
|[CDatabase::CommitTrans](../Topic/CDatabase::CommitTrans.md)|Completa una transacción iniciada por **BeginTrans**.  Modifican los comandos en la transacción que modifica el origen de datos.|  
|[CDatabase::ExecuteSQL](../Topic/CDatabase::ExecuteSQL.md)|ejecuta una instrucción SQL.  No se devuelve ningún registro de datos.|  
|[CDatabase::GetBookmarkPersistence](../Topic/CDatabase::GetBookmarkPersistence.md)|Identifica las operaciones con las que los marcadores conservan en objetos de conjunto de registros.|  
|[CDatabase::GetConnect](../Topic/CDatabase::GetConnect.md)|devuelve la cadena de conexión ODBC utilizada para conectar el objeto de `CDatabase` a un origen de datos.|  
|[CDatabase::GetCursorCommitBehavior](../Topic/CDatabase::GetCursorCommitBehavior.md)|Identifica el efecto de confirmar una transacción en un objeto de conjunto de registros abierto.|  
|[CDatabase::GetCursorRollbackBehavior](../Topic/CDatabase::GetCursorRollbackBehavior.md)|Identifica el efecto de reserva de revertir una transacción en un objeto de conjunto de registros abierto.|  
|[CDatabase::GetDatabaseName](../Topic/CDatabase::GetDatabaseName.md)|devuelve el nombre de la base de datos actualmente en uso.|  
|[CDatabase::IsOpen](../Topic/CDatabase::IsOpen.md)|Devuelve cero si el objeto de `CDatabase` está conectado actualmente a un origen de datos.|  
|[CDatabase::OnSetOptions](../Topic/CDatabase::OnSetOptions.md)|Llamado por el marco para establecer opciones de conexión estándar.  la implementación predeterminada establece el valor de tiempo de espera de la consulta.  Puede establecer estas opciones antes de tiempo llamando a `SetQueryTimeout`.|  
|[CDatabase::Open](../Topic/CDatabase::Open.md)|Establece una conexión a un origen de datos \(mediante un controlador ODBC\).|  
|[CDatabase::OpenEx](../Topic/CDatabase::OpenEx.md)|Establece una conexión a un origen de datos \(mediante un controlador ODBC\).|  
|[CDatabase::Rollback](../Topic/CDatabase::Rollback.md)|Cambios de los invierte realizados durante la transacción actual.  el origen de datos vuelve a su estado anterior, como definido en la llamada de **BeginTrans** , inalterada.|  
|[CDatabase::SetLoginTimeout](../Topic/CDatabase::SetLoginTimeout.md)|Establece el número de segundos después del cual se ha de un tiempo de espera del intento de conexión a un origen de datos.|  
|[CDatabase::SetQueryTimeout](../Topic/CDatabase::SetQueryTimeout.md)|Establece el número de segundos después del cual se ha de tiempo de espera se de operaciones de consulta de base de datos.  Afecta a todo el conjunto de registros posterior **Abrir**, `AddNew`, llamadas a **Editar**, y de **Eliminar** .|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDatabase::m\_hdbc](../Topic/CDatabase::m_hdbc.md)|Identificador de la conexión de ODBC a un origen de datos.  tipo **HDBC**.|  
  
## Comentarios  
 Un origen de datos es una instancia específica de datos hospedados en otro Sistema de administración de bases de datos \(DBMS\).  Incluyen Microsoft SQL Server samples, dBASE de Microsoft Access, de Borland, y xBASE.  Puede tener activo de uno o más objetos de `CDatabase` al mismo tiempo en la aplicación.  
  
> [!NOTE]
>  Si trabaja con las clases \(DAO\) de Objetos de acceso a datos en lugar de las clases de ODBC, utilice la clase [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) en su lugar.  Para obtener más información, vea el artículo [información general: programación de la base de datos](../../data/data-access-programming-mfc-atl.md).  
  
 Para utilizar `CDatabase`, crear un objeto de `CDatabase` y llamar a su función miembro de `OpenEx` .  esto abre una conexión.  Cuando se construye los objetos de `CRecordset` para trabajar en el origen de datos conectado, pase al constructor de conjunto de registros un puntero al objeto de `CDatabase` .  Cuando termine de usar la conexión, llame a la función miembro de **Cerrar** y destruya el objeto de `CDatabase` .  **Cerrar** cierra cualquier conjunto de registros que no ha cerrado previamente.  
  
 Para obtener más información sobre `CDatabase`, vea los artículos [origen de datos \(ODBC\)](../../data/odbc/data-source-odbc.md) y [información general: programación de la base de datos](../../data/data-access-programming-mfc-atl.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDatabase`  
  
## Requisitos  
 **encabezado:** afxdb.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)