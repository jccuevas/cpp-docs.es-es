---
title: "CDaoTableDef Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDaoTableDef"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoTableDef class"
  - "clases de base de datos [C++], DAO"
  - "database tables [C++], attached table definition"
  - "database tables [C++], base table definition"
  - "tabledefs [C++]"
ms.assetid: 7c5d2254-8475-43c4-8a6c-2d32ead194c9
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoTableDef Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa la definición almacenada de una tabla base o tabla asociada.  
  
## Sintaxis  
  
```  
class CDaoTableDef : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoTableDef::CDaoTableDef](../Topic/CDaoTableDef::CDaoTableDef.md)|construye un objeto de **CDaoTableDef** .|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoTableDef::Append](../Topic/CDaoTableDef::Append.md)|Agrega una nueva tabla en la base de datos.|  
|[CDaoTableDef::CanUpdate](../Topic/CDaoTableDef::CanUpdate.md)|Devuelve cero si la tabla puede actualizarse \(puede modificar la definición de campos o propiedades de la tabla\).|  
|[CDaoTableDef::Close](../Topic/CDaoTableDef::Close.md)|Cierra un definición abierto.|  
|[CDaoTableDef::Create](../Topic/CDaoTableDef::Create.md)|Crea una tabla que se puede agregar a la base de datos con [Anexar](../Topic/CDaoTableDef::Append.md).|  
|[CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md)|Denominado para crear un campo de una tabla.|  
|[CDaoTableDef::CreateIndex](../Topic/CDaoTableDef::CreateIndex.md)|Denominado para crear un índice de una tabla.|  
|[CDaoTableDef::DeleteField](../Topic/CDaoTableDef::DeleteField.md)|denominado para eliminar un campo de una tabla.|  
|[CDaoTableDef::DeleteIndex](../Topic/CDaoTableDef::DeleteIndex.md)|denominado para eliminar un índice de una tabla.|  
|[CDaoTableDef::GetAttributes](../Topic/CDaoTableDef::GetAttributes.md)|Devuelve un valor que indica una o más características de un objeto de `CDaoTableDef` .|  
|[CDaoTableDef::GetConnect](../Topic/CDaoTableDef::GetConnect.md)|Devuelve un valor que proporciona información sobre el origen de una tabla.|  
|[CDaoTableDef::GetDateCreated](../Topic/CDaoTableDef::GetDateCreated.md)|Devuelve la fecha y hora en que la tabla base que era la base de un objeto de `CDaoTableDef` se creó.|  
|[CDaoTableDef::GetDateLastUpdated](../Topic/CDaoTableDef::GetDateLastUpdated.md)|Devuelve la fecha y hora de cambio realizado más reciente en el diseño de la tabla base.|  
|[CDaoTableDef::GetFieldCount](../Topic/CDaoTableDef::GetFieldCount.md)|Devuelve un valor que representa el número de campos de la tabla.|  
|[CDaoTableDef::GetFieldInfo](../Topic/CDaoTableDef::GetFieldInfo.md)|Devuelve los tipos de información concreta sobre los campos en la tabla.|  
|[CDaoTableDef::GetIndexCount](../Topic/CDaoTableDef::GetIndexCount.md)|Devuelve el número de índices de la tabla.|  
|[CDaoTableDef::GetIndexInfo](../Topic/CDaoTableDef::GetIndexInfo.md)|Devuelve los tipos de información concreta sobre los índices de la tabla.|  
|[CDaoTableDef::GetName](../Topic/CDaoTableDef::GetName.md)|devuelve el nombre definido por el usuario de la tabla.|  
|[CDaoTableDef::GetRecordCount](../Topic/CDaoTableDef::GetRecordCount.md)|Devuelve el número de registros de la tabla.|  
|[CDaoTableDef::GetSourceTableName](../Topic/CDaoTableDef::GetSourceTableName.md)|Devuelve un valor que especifica el nombre de la tabla asociada en la base de datos de origen.|  
|[CDaoTableDef::GetValidationRule](../Topic/CDaoTableDef::GetValidationRule.md)|Devuelve un valor que valide los datos en un campo mientras se cambia o se agrega a una tabla.|  
|[CDaoTableDef::GetValidationText](../Topic/CDaoTableDef::GetValidationText.md)|Devuelve un valor que especifica el texto del mensaje que la aplicación muestra si el valor de un objeto de campo no cumple la regla de validación especificada.|  
|[CDaoTableDef::IsOpen](../Topic/CDaoTableDef::IsOpen.md)|Devuelve cero si la tabla está abierto.|  
|[CDaoTableDef::Open](../Topic/CDaoTableDef::Open.md)|Abra un definición existente almacenado en la colección de Definición de base de datos.|  
|[CDaoTableDef::RefreshLink](../Topic/CDaoTableDef::RefreshLink.md)|Actualiza la información de conexión para una tabla asociada.|  
|[CDaoTableDef::SetAttributes](../Topic/CDaoTableDef::SetAttributes.md)|Establece un valor que indica una o más características de un objeto de `CDaoTableDef` .|  
|[CDaoTableDef::SetConnect](../Topic/CDaoTableDef::SetConnect.md)|Establece un valor que proporciona información sobre el origen de una tabla.|  
|[CDaoTableDef::SetName](../Topic/CDaoTableDef::SetName.md)|establece el nombre de la tabla.|  
|[CDaoTableDef::SetSourceTableName](../Topic/CDaoTableDef::SetSourceTableName.md)|Establece un valor que especifica el nombre de una tabla asociada en la base de datos de origen.|  
|[CDaoTableDef::SetValidationRule](../Topic/CDaoTableDef::SetValidationRule.md)|Establece un valor que valide los datos en un campo mientras se cambia o se agrega a una tabla.|  
|[CDaoTableDef::SetValidationText](../Topic/CDaoTableDef::SetValidationText.md)|Establece un valor que especifica el texto del mensaje que la aplicación muestra si el valor de un objeto de campo no cumple la regla de validación especificada.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoTableDef::m\_pDAOTableDef](../Topic/CDaoTableDef::m_pDAOTableDef.md)|Un puntero a la interfaz de DAO al objeto de definición.|  
|[CDaoTableDef::m\_pDatabase](../Topic/CDaoTableDef::m_pDatabase.md)|base de datos de origen para esta tabla.|  
  
## Comentarios  
 Cada objeto de base de datos de DAO mantiene una colección, denominada TableDefs, que contiene todos los objetos guardados de definición de DAO.  
  
 Se manipula una definición de tabla utilizando un objeto de `CDaoTableDef` .  Por ejemplo, puede:  
  
-   Examine la estructura del campo y de índice de cualquier valor local, asociada, o la tabla externa en una base de datos.  
  
-   Llame a las funciones miembro de `SetConnect` y de `SetSourceTableName` para las tablas asociadas, y utilice la función miembro de `RefreshLink` para actualizar conexiones a las tablas asociadas.  
  
-   Llame a la función miembro de `CanUpdate` para determinar si puede modificar definiciones de campo de la tabla.  
  
-   Obtiene o fije las condiciones de la validación mediante `GetValidationRule` y `SetValidationRule`, y el miembro de `GetValidationText` y de `SetValidationText` funciona.  
  
-   Utilice la función miembro de **Abrir** para crear una tabla, un dynaset\-, o un objeto de `CDaoRecordset` de tipo instantánea.  
  
    > [!NOTE]
    >  Las clases de base de datos de DAO son distintas de las clases de base de datos MFC basadas en ODBC.  Todos los nombres de clase de base de datos de DAO tienen el prefijo “CDao”.  Todavía puede tener acceso a orígenes de datos ODBC con las clases DAO; las clases DAO suelen proporcionar capacidades máximas porque son específicas del motor de base de datos Microsoft Jet.  
  
### Para utilizar objetos de definición para trabajar con una tabla existente o crear una nueva tabla  
  
1.  En todos los casos, primero cree un objeto de `CDaoTableDef` , proporcionando un puntero a un objeto de [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) al que la tabla pertenece.  
  
2.  Haga lo siguiente, en función de lo que desea:  
  
    -   Para utilizar un existente guardado la tabla, llame a la función miembro de [Abrir](../Topic/CDaoTableDef::Open.md) del objeto de definición, proporcionando el nombre de la tabla guardada.  
  
    -   Para crear una nueva tabla, llame a la función miembro de [Crear](../Topic/CDaoTableDef::Create.md) del objeto de definición, proporcionando el nombre de la tabla.  Llame a [CreateField](../Topic/CDaoTableDef::CreateField.md) y [CreateIndex](../Topic/CDaoTableDef::CreateIndex.md) para agregar campos e índices de la tabla.  
  
    -   Llame a [Anexar](../Topic/CDaoTableDef::Append.md) para guardar la tabla y se anexa a la colección de TableDefs de base de datos.  **Crear** coloca el definición en un estado abierto, por lo que después de llamar a **Crear** que no llama **Abrir**.  
  
        > [!TIP]
        >  La manera más fácil de crear tablas guardadas es crearlas y almacenar en la base de datos mediante Microsoft Access.  Puede abrir y utilizarlos en el código de MFC.  
  
 Para utilizar el objeto de definición que se ha abierto o creado, crear y abrir un objeto de `CDaoRecordset` , especificando el nombre de definición con un valor de **dbOpenTable** en el parámetro de `nOpenType` .  
  
 Para utilizar un objeto de definición para crear un objeto de `CDaoRecordset` , cree o abra un definición como se describió anteriormente, después crea normalmente un objeto de conjunto de registros, pasar un puntero al objeto de definición cuando se llama a [CDaoRecordset:: Abrir](../Topic/CDaoRecordset::Open.md).  La definición que pasa debe estar en un estado abierto.  Para obtener más información, vea la clase [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).  
  
 Cuando termine de usar un objeto de definición, llame a su función miembro de [Cerrar](../Topic/CDaoRecordset::Close.md) ; a continuación destruya el objeto de definición.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoTableDef`  
  
## Requisitos  
 **encabezado:** afxdao.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDaoDatabase Class](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoRecordset Class](../../mfc/reference/cdaorecordset-class.md)