---
title: 'Intercambio de campos de registros: Utilizar RFX | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0a1a30b1643127f1451654f5bdaf3edfa56896bc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="record-field-exchange-using-rfx"></a>Intercambio de campos de registros: Utilizar RFX
Este tema explica qué hacer para utilizar RFX en función de lo que hace el marco de trabajo.  
  
> [!NOTE]
>  En este tema se aplica a las clases derivadas de [CRecordset](../../mfc/reference/crecordset-class.md) qué masiva de filas no se ha implementado la obtención. Si se utiliza la obtención masiva de filas, se implementa el intercambio masivo de campos de registros (RFX masivo). RFX masivo es similar a RFX. Para entender las diferencias, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Los temas siguientes contienen información relacionada:  
  
-   [Intercambio de campos de registros: Trabajar con el código de asistente](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md) presenta los principales componentes de RFX y explica el código que el Asistente para aplicaciones MFC y **Agregar clase** (como se describe en [agregar un consumidor ODBC de MFC ](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) para la compatibilidad con RFX y cómo desea modificar el código del asistente.  
  
-   [Intercambio de campos de registros: Utilizar las funciones de RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md) explica cómo escribir llamadas a las funciones de RFX en su `DoFieldExchange` invalidar.  
  
 En la tabla siguiente se muestra su rol en relación con lo que hace el marco de trabajo para usted.  
  
### <a name="using-rfx-you-and-the-framework"></a>Usar RFX: El programador y el marco de trabajo  
  
|El programador|El marco de trabajo|  
|---------|-------------------|  

| Declarar las clases de conjunto de registros mediante un asistente. Especificar nombres y tipos de datos de miembros de datos de campo. | El asistente crea un `CRecordset` clase y las escrituras un [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) invalidar para usted, incluyendo un RFX función llamada para cada miembro de datos de campo. |  
| (Opcional) Agregar manualmente los miembros de datos de parámetro necesarios a la clase. Agregar manualmente una llamada de función RFX a `DoFieldExchange` para cada miembro de datos de parámetro, agregue una llamada a [CFieldExchange:: SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) para el grupo de parámetros y especifique el número total de parámetros en [m_nParams ](../../mfc/reference/crecordset-class.md#m_nparams). Vea [conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md). ||  
| (Opcional) Enlazar manualmente columnas adicionales a los miembros de datos de campo. Incrementar manualmente [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields). Vea [conjunto de registros: enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md). ||  

| Construir un objeto de la clase de conjunto de registros. Antes de usar el objeto, establecer los valores del parámetro de miembros de datos, si lo hay. | Para mejorar la eficacia, el marco de trabajo prebinds los parámetros, con ODBC. Al pasar valores de parámetro, el marco de trabajo pasa al origen de datos. Solo los valores de parámetro se envían nuevas consultas, a menos que se han cambiado las cadenas de ordenación o filtro. |  
| Abrir un objeto de conjunto de registros mediante [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open). | Ejecuta la consulta del conjunto de registros, enlaza las columnas a los miembros de datos de campo del conjunto de registros y las llamadas `DoFieldExchange` para intercambiar datos entre el primer registro seleccionado y los miembros de datos de campo del conjunto de registros. |  
| Desplazamiento en el conjunto de registros mediante [CRecordset:: Move](../../mfc/reference/crecordset-class.md#move) o un comando de menú o barra de herramientas. | Llamadas `DoFieldExchange` para transferir datos a los miembros de datos de campo desde el nuevo registro actual. |  
| Agregar, actualizar y eliminar registros. | Llamadas `DoFieldExchange` para transferir datos al origen de datos. |  
  
## <a name="see-also"></a>Vea también  
 [Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)   
 [Intercambio de campos de registros: Funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)   
 [Conjunto de registros: Obtener cálculos SUM y otros resultados agregados (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)   
 [CRecordset (clase)](../../mfc/reference/crecordset-class.md)   
 [Clase CFieldExchange](../../mfc/reference/cfieldexchange-class.md)   
 [Macros, funciones globales y Variables globales](../../mfc/reference/mfc-macros-and-globals.md)

