---
title: "CFieldExchange Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFieldExchange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFieldExchange class"
  - "tipos de datos [C++], custom"
  - "enum FieldType"
  - "enum FieldType, CFieldExchange"
  - "FieldType enumeration"
  - "RFX (record field exchange) [C++]"
  - "RFX (record field exchange) [C++], classes for"
ms.assetid: 24c5c0b3-06a6-430e-9b6f-005a2c65e29f
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CFieldExchange Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Admite las rutinas de registro de intercambio de campos de registros \(RFX\) y de intercambio de campos de registros \(RFX Masivo\) utilizadas por las clases de base de datos.  
  
## Sintaxis  
  
```  
  
class CFieldExchange  
  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFieldExchange::IsFieldType](../Topic/CFieldExchange::IsFieldType.md)|Devuelve cero si la operación actual es adecuada para el tipo de campo que está actualizado.|  
|[CFieldExchange::SetFieldType](../Topic/CFieldExchange::SetFieldType.md)|Especifica el tipo de conjunto de registros que el miembro de datos o columna o parámetro — representado por todas las llamadas de siguiente a RFX funciona hasta la siguiente llamada a `SetFieldType`.|  
  
## Comentarios  
 `CFieldExchange` no tiene una clase base.  
  
 Utilice esta clase si escribe las rutinas de intercambio de datos para los tipos de datos personalizados o cuando se implementa la obtención masiva de filas; si no, no utilizará directamente esta clase.  Datos de intercambios de RFX y RFX masivo entre los miembros de datos de campo del objeto de conjunto de registros y los campos correspondientes del registro actual en el origen de datos.  
  
> [!NOTE]
>  Si trabaja con Objetos de acceso a datos que \(DAO\) ordena en lugar de las clases de ODBC, clase [CDaoFieldExchange](../../mfc/reference/cdaofieldexchange-class.md) de uso en su lugar.  Para obtener más información, vea el artículo [información general: programación de la base de datos](../../data/data-access-programming-mfc-atl.md).  
  
 Un objeto de `CFieldExchange` proporciona información de contexto necesaria para que el intercambio de campos de intercambio de campos o de registro de cola tenga lugar.  Los objetos de`CFieldExchange` admiten varias operaciones, incluidos los miembros obligatorios de los parámetros y de datos de campo y marcas de valores distintos en los campos del registro actual.  Las operaciones RFX y RFX masivo se realizan en los miembros de datos del conjunto de registros\- clase de tipos definidos por `enum`**FieldType** en `CFieldExchange`.  Los valores posibles de **FieldType** son:  
  
-   **CFieldExchange::outputColumn** para los miembros de datos de campo.  
  
-   **CFieldExchange::inputParam** o **CFieldExchange::param** para los miembros de datos del parámetro de entrada.  
  
-   **CFieldExchange::outputParam** para los miembros de datos de parámetro de salida.  
  
-   **CFieldExchange::inoutParam** para los miembros de datos de parámetro de entrada\/salida.  
  
 La mayoría de proporcionan las funciones y los miembros de datos de miembros de la clase para escribir sus propias rutinas personalizados de RFX.  Utilizará `SetFieldType` con frecuencia.  Para obtener más información, vea los artículos [Intercambio de campos de registros](../../data/odbc/record-field-exchange-rfx.md) y [conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md).  Para obtener información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: Obtener registros de forma masiva \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  Para obtener más información sobre las funciones globales de RFX y RFX masivo, vea [Grabe las funciones de Intercambio de campo](../../mfc/reference/record-field-exchange-functions.md) en la sección de macros y Globals MFC de esta referencia.  
  
## Jerarquía de herencia  
 `CFieldExchange`  
  
## Requisitos  
 **encabezado:** afxdb.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)