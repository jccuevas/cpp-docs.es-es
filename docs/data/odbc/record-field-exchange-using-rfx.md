---
title: "Intercambio de campos de registros: Utilizar RFX | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RFX (ODBC), implementar"
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Intercambio de campos de registros: Utilizar RFX
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema explica los pasos necesarios para utilizar RFX en función de lo que hace el marco de trabajo.  
  
> [!NOTE]
>  Este tema es aplicable a las clases derivadas de [CRecordset](../../mfc/reference/crecordset-class.md) donde la obtención masiva de filas no está implementada.  Si usa esta obtención masiva, se implementará el intercambio masivo de campos de registros \(RFX masivo\).  RFX masivo es similar a RFX.  Para comprender mejor estas diferencias, vea [Conjunto de registros: Obtener registros de forma masiva \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Los temas siguientes contienen información relacionada:  
  
-   [Intercambio de campos de registros: trabajar con el código de asistente](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md) presenta los principales componentes de RFX y explica el código generado por el Asistente para aplicaciones MFC y el comando **Agregar clase** \(como se describe en [Agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)\) para la compatibilidad con RFX, y cuándo resulta conveniente modificar el código del asistente.  
  
-   [Intercambio de campos de registros: usar las funciones de RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md) explica cómo escribir llamadas a las funciones de RFX en la función de reemplazo de `DoFieldExchange`.  
  
 La tabla siguiente muestra el rol del programador teniendo en cuenta lo que aporta el marco de trabajo.  
  
### Usar RFX: el programador y el marco de trabajo  
  
|El programador|El marco de trabajo|  
|--------------------|-------------------------|  
|Declara las clases de conjuntos de registros mediante un asistente.  Especifica los nombres y tipos de datos de los miembros de datos de campo.|El asistente crea una clase derivada de `CRecordset` y escribe una función de reemplazo de [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md), incluida una llamada de función RFX por cada uno de los miembros de datos de campo.|  
|\(Opcional\) Agrega manualmente los miembros de datos de parámetro necesarios a la clase.  Agrega manualmente una llamada de función RFX a `DoFieldExchange` por cada miembro de datos de parámetro, agrega una llamada a [CFieldExchange::SetFieldType](../Topic/CFieldExchange::SetFieldType.md) para el grupo de parámetros y especifica el número total de parámetros en [m\_nParams](../Topic/CRecordset::m_nParams.md).  Vea [Conjunto de registros: Parametrizar un conjunto de registros \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).||  
|\(Opcional\) Enlaza manualmente columnas adicionales con los miembros de datos de campo.  Aumenta manualmente [m\_nFields](../Topic/CRecordset::m_nFields.md).  Vea [Conjunto de registros: enlazar dinámicamente columnas de datos \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)||  
|Crea un objeto de la clase de conjunto de registros.  Antes de usar el objeto, establece los valores de sus miembros de datos de parámetro, si los hay.|Por motivos de eficacia, el marco de trabajo realiza un enlace previo de los parámetros, usando ODBC.  Al pasar los valores de parámetro, el marco de trabajo los pasa a su vez al origen de datos.  En consultas repetidas, sólo se envían los valores de parámetros, excepto si ha cambiado las cadenas de filtro y orden.|  
|Abre un objeto de conjunto de registros usando [CRecordset::Open](../Topic/CRecordset::Open.md).|Ejecuta la consulta del conjunto de registros, enlaza las columnas a los miembros de datos de campo del mismo y llama a `DoFieldExchange` para intercambiar datos entre el primer registro seleccionado y los miembros de datos de campo del conjunto de registros.|  
|Se desplaza en el conjunto de registros mediante [CRecordset::Move](../Topic/CRecordset::Move.md) o un comando de menú o de barra de herramientas.|Llama a `DoFieldExchange` para transferir datos a los miembros de datos de campo desde el nuevo registro actual.|  
|Agrega, actualiza y elimina registros.|Llama a `DoFieldExchange` para transferir datos hacia el origen de datos.|  
  
## Vea también  
 [Intercambio de campos de registros \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)   
 [Intercambio de campos de registros: Funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)   
 [Conjunto de registros: Obtener cálculos SUM y otros resultados agregados \(ODBC\)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)   
 [CFieldExchange Class](../../mfc/reference/cfieldexchange-class.md)   
 [Macros, funciones globales y variables globales](../Topic/Macros,%20Global%20Functions,%20and%20Global%20Variables.md)