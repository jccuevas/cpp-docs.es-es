---
title: "CDaoFieldExchange Class | Microsoft Docs"
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
  - "CDaoFieldExchange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoFieldExchange class"
  - "DAO (objetos de acceso a datos), record field exchange (DFX)"
  - "DFX (intercambio de campos de registros DAO)"
  - "DFX (intercambio de campos de registros DAO), DAO Record Field Exchange"
  - "exchanging data between databases and recordsets"
  - "field exchange"
  - "field exchange, record for DAO classes"
  - "RFX (intercambio de campos de registros)"
  - "RFX (intercambio de campos de registros), clases DAO"
ms.assetid: 350a663e-92ff-44ab-ad53-d94efa2e5823
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoFieldExchange Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Admite las rutinas de intercambio de campos del registro de DAO \(DFX\) utilizadas por las clases de base de datos de DAO.  
  
## Sintaxis  
  
```  
class CDaoFieldExchange  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoFieldExchange::IsValidOperation](../Topic/CDaoFieldExchange::IsValidOperation.md)|Devuelve cero si la operación actual es adecuada para el tipo de campo que está actualizado.|  
|[CDaoFieldExchange::SetFieldType](../Topic/CDaoFieldExchange::SetFieldType.md)|Especifica el tipo de conjunto de registros que el miembro de datos o columna o parámetro — representado por todas las llamadas subsiguientes a DFX funciona hasta la siguiente llamada a `SetFieldType`.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoFieldExchange::m\_nOperation](../Topic/CDaoFieldExchange::m_nOperation.md)|La operación de DFX que realiza la llamada actual a la función miembro de `DoFieldExchange` de conjunto de registros.|  
|[CDaoFieldExchange::m\_prs](../Topic/CDaoFieldExchange::m_prs.md)|Un puntero al conjunto de registros en el que se realizan las operaciones de DFX.|  
  
## Comentarios  
 `CDaoFieldExchange` no tiene una clase base.  
  
 Utilice esta clase si escribe las rutinas de intercambio de datos para los tipos de datos personalizados; si no, no utilizará directamente esta clase.  Datos de intercambios de DFX entre los miembros de datos de campo del objeto de [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) y los campos correspondientes del registro actual en el origen de datos.  DFX administra el intercambio en ambas direcciones, del origen de datos y el origen de datos.  Vea [nota técnica 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) para obtener información sobre las rutinas personalizadas de escritura DFX.  
  
> [!NOTE]
>  Las clases de base de datos de DAO son distintas de las clases de base de datos MFC basadas en ODBC.  Todos los nombres de clase de base de datos de DAO tienen el prefijo “CDao”.  Todavía puede tener acceso a orígenes de datos ODBC con las clases DAO.  las clases MFC basadas en DAO son generalmente más capaces que las clases MFC basadas en ODBC.  Las clases DAO\- basadas pueden tener acceso a los datos, incluidos mediante controladores ODBC, a través de su propio motor de base de datos.  También admiten las operaciones de \(DDL\) de lenguaje de definición de datos, como tablas de suma mediante las clases en lugar de tener que llamar a DAO personalmente.  
  
> [!NOTE]
>  El intercambio de campos del registro de DAO \(DFX\) es muy similar al intercambio de campos de registros \(RFX\) en clases ODBC\- basadas de base de datos de MFC \(`CDatabase`, `CRecordset`\).  Si entiende RFX, se le resultará DFX fácil de usar.  
  
 Un objeto de `CDaoFieldExchange` proporciona información de contexto necesaria para que el intercambio de campos del registro de DAO tenga lugar.  Los objetos de`CDaoFieldExchange` admiten varias operaciones, incluidos los miembros obligatorios de los parámetros y de datos de campo y marcas de valores distintos en los campos del registro actual.  Las operaciones de DFX se realizan en los miembros de datos del conjunto de registros\- clase de tipos definidos por `enum`**FieldType** en `CDaoFieldExchange`.  Los valores posibles de **FieldType** son:  
  
-   **CDaoFieldExchange::outputColumn** para los miembros de datos de campo.  
  
-   **CDaoFieldExchange::param** para los miembros de datos de parámetro.  
  
 La función miembro de [IsValidOperation](../Topic/CDaoFieldExchange::IsValidOperation.md) se proporciona para escribir sus propias rutinas de custom DFX.  Utilizará [SetFieldType](../Topic/CDaoFieldExchange::SetFieldType.md) con frecuencia en las funciones de [CDaoRecordset::DoFieldExchange](../Topic/CDaoRecordset::DoFieldExchange.md) .  Para obtener más información sobre las funciones globales de DFX, vea [Funciones de intercambio de campos](../../mfc/reference/record-field-exchange-functions.md).  Para obtener información sobre las rutinas personalizadas de escritura DFX para sus propios tipos de datos, vea [nota técnica 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).  
  
## Jerarquía de herencia  
 `CDaoFieldExchange`  
  
## Requisitos  
 **encabezado:** afxdao.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset Class](../../mfc/reference/cdaorecordset-class.md)