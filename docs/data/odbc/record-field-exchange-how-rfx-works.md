---
title: "Intercambio de campos de registros: Funcionamiento de RFX | Microsoft Docs"
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
  - "enlace de datos [C++], DFX"
  - "ODBC [C++], RFX"
  - "edición de registros [C++], utilizar RFX"
  - "RFX (ODBC) [C++], enlazar campos y parámetros"
  - "RFX (ODBC) [C++], actualizar datos en conjuntos de registros"
  - "desplazarse [C++]"
  - "desplazarse [C++], RFX"
ms.assetid: e647cacd-62b0-4b80-9e20-b392deca5a88
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Intercambio de campos de registros: Funcionamiento de RFX
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema explica el proceso RFX.  Éste es un tema avanzado que trata:  
  
-   [RFX y el conjunto de registros](#_core_rfx_and_the_recordset)  
  
-   [El proceso RFX](#_core_the_record_field_exchange_process)  
  
> [!NOTE]
>  Este tema se aplica a clases derivadas de `CRecordset` donde no se haya implementado la obtención masiva de filas.  Si usa esta obtención masiva, se implementará el intercambio masivo de campos de registros \(RFX masivo\).  RFX masivo es similar a RFX.  Para comprender mejor estas diferencias, vea [Conjunto de registros: Obtener registros de forma masiva \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_rfx_and_the_recordset"></a> RFX y el conjunto de registros  
 Los miembros de datos de campo del objeto de conjunto de registros, tomados juntos, constituyen un búfer de edición que contiene las columnas seleccionadas de un registro.  Cuando se abre por primera vez el conjunto de registros y está a punto de leer el primer registro, RFX enlaza \(asocia\) cada una de las columnas seleccionadas con la dirección del miembro de datos de campo correspondiente.  Cuando el conjunto de registros actualiza un registro, RFX llama a funciones de la API ODBC para enviar una instrucción SQL **UPDATE** o **INSERT** al controlador.  RFX utiliza su conocimiento de los miembros de datos de campo para especificar las columnas que se han de escribir.  
  
 El marco de trabajo realiza una copia de seguridad del búfer de edición en determinados momentos para poder restaurar su contenido si es necesario.  RFX hace una copia de seguridad del búfer de edición antes de agregar un nuevo registro y antes de editar un registro existente.  Restaura el búfer de edición en algunos casos, por ejemplo, después de una llamada a `AddNew` seguida de una llamada a **Update.** En cambio, no se restaura si se deja un búfer recién modificado desplazándose, por ejemplo, a otro registro antes de llamar a **Update**.  
  
 Además de intercambiar datos entre el origen de datos y los miembros de datos de campo del conjunto de registros, RFX administra el enlace de parámetros.  Cuando se abre el conjunto de registros, todos los miembros de datos de parámetro se enlazan siguiendo el orden de los marcadores de posición "?" en la instrucción SQL que `CRecordset::Open` crea.  Para obtener más información, vea [Conjunto de registros: Parametrizar un conjunto de registros \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
 El reemplazo de la clase de conjunto de registros para `DoFieldExchange` hace todo el trabajo, moviendo los datos en ambas direcciones.  Al igual que el intercambio de datos de cuadros de diálogo \(DDX\), RFX necesita información sobre los miembros de datos de la clase.  El asistente proporciona la información necesaria escribiendo una implementación específica del conjunto de registros `DoFieldExchange`, basada en los nombres y tipos de datos de los miembros de datos de campo especificados mediante el asistente.  
  
##  <a name="_core_the_record_field_exchange_process"></a> Proceso de intercambio de campos de registros  
 Esta sección describe la secuencia de eventos de RFX al abrirse un objeto de conjunto de registros y agregar, actualizar o eliminar registros.  Las tablas [Secuencia de operaciones RFX durante la apertura de un conjunto de registros](#_core_sequence_of_rfx_operations_during_recordset_open) y [Secuencia de operaciones RFX durante el desplazamiento](#_core_sequence_of_rfx_operations_during_scrolling), en este tema, muestran el proceso por el que RFX procesa un comando **Move** en el conjunto de registros y administra una actualización.  Durante esos procesos, se llama a [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) para realizar varias operaciones diferentes.  El miembro de datos **m\_nOperation** del objeto [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) determina qué operación se solicita.  Puede ser útil leer [Conjunto de registros: Cómo se seleccionan los registros \(ODBC\)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) y [Conjunto de registros: Actualizar los registros \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) antes de leer este material.  
  
###  <a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a> RFX: enlace inicial de columnas y parámetros  
 Al llamar a la función miembro [Open](../Topic/CRecordset::Open.md) de un objeto de conjunto de registros se producen las siguientes actividades de RFX, en el orden mostrado:  
  
-   Si el conjunto de registros contiene miembros de datos de parámetro, el marco de trabajo llama a `DoFieldExchange` para enlazar los parámetros con marcadores de posición de parámetro en la cadena de la instrucción SQL del conjunto de registros.  Se utiliza una representación, dependiente del tipo de datos, del valor del parámetro para cada marcador de posición existente en la instrucción **SELECT**.  Esto ocurre una vez que está preparada la instrucción SQL, pero antes de ejecutarse.  Para obtener más información sobre la preparación de instrucciones, vea la función **::SQLPrepare** en la *Referencia del programador* de ODBC.  
  
-   El marco de trabajo llama a `DoFieldExchange` una segunda vez para enlazar los valores de las columnas seleccionadas con los miembros de datos correspondientes en el conjunto de registros.  Ello establece el objeto de conjunto de registros como un búfer de edición que contiene las columnas del primer registro.  
  
-   El conjunto de registros ejecuta la instrucción SQL y el origen de datos selecciona el primer registro.  A continuación, las columnas del registro se cargan en los miembros de datos de campo del conjunto de registros.  
  
 La tabla siguiente muestra la secuencia de operaciones RFX al abrir un conjunto de registros.  
  
### Secuencia de operaciones RFX durante la apertura de un conjunto de registros  
  
|Operación|Operación DoFieldExchange|Operación de base de datos\/SQL|  
|---------------|-------------------------------|-------------------------------------|  
|1.  Abrir el conjunto de registros.|||  
||2.  Compilar una instrucción SQL.||  
|||3.  Enviar el código SQL.|  
||4.  Enlazar miembros de datos de parámetros.||  
||5.  Enlazar miembros de datos de campo con columnas.||  
|||6.  ODBC realiza el traslado y aporta los datos.|  
||7.  Corregir los datos correspondientes a C\+\+.||  
  
 Los conjuntos de registros usan la ejecución preparada de ODBC para permitir nuevas consultas con rapidez usando la misma instrucción SQL.  Para obtener más información sobre la ejecución preparada, vea la *Referencia del programador* del SDK de ODBC en MSDN Library.  
  
###  <a name="_mfc_rfx.3a_.scrolling"></a> RFX: desplazamiento  
 Al desplazarse de un registro a otro, el marco de trabajo llama a `DoFieldExchange` para reemplazar los valores almacenados previamente en los miembros de datos de campo por los valores del nuevo registro.  
  
 La tabla siguiente muestra la secuencia de operaciones RFX cuando el usuario se traslada de un registro a otro.  
  
### Secuencia de las operaciones RFX durante el desplazamiento  
  
|Operación|Operación DoFieldExchange|Operación de base de datos\/SQL|  
|---------------|-------------------------------|-------------------------------------|  
|1.  Llamar a `MoveNext` o a una de las demás funciones Move.|||  
|||2.  ODBC realiza el traslado y aporta los datos.|  
||3.  Corregir los datos correspondientes a C\+\+.||  
  
###  <a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a> RFX: agregar nuevos registros y editar los registros existentes  
 Si agrega un nuevo registro, el conjunto de registros funciona como un búfer de edición para compilar el contenido del nuevo registro.  Al igual que sucede cuando se agregan registros, editar registros implica modificar los valores de los miembros de datos de campo del conjunto de registros.  Desde la perspectiva de RFX, la secuencia es la siguiente:  
  
1.  La llamada a la función miembro [AddNew](../Topic/CRecordset::AddNew.md) o [Edit](../Topic/CRecordset::Edit.md) del conjunto de registros hace que RFX almacene el búfer de edición actual con el fin de poder restaurarse más tarde.  
  
2.  `AddNew` o **Edit** preparan los campos en el búfer de edición para que RFX pueda detectar los miembros de datos de campo modificados.  
  
     Puesto que un nuevo registro no tiene valores anteriores con los que comparar los nuevos, `AddNew` establece el valor de todos los miembros de datos de campo en un valor **PSEUDO\_NULL**.  Más tarde, al llamar a **Update**, RFX compara el valor de cada uno de los miembros de datos con el valor **PSEUDO\_NULL**.  Si hay alguna diferencia, significa que se estableció el valor del miembro de datos. \(**PSEUDO\_NULL** no es lo mismo que una columna de registro con un valor Null real, y tampoco ninguno de ellos equivale al tipo **NULL** de C\+\+\).  
  
     A diferencia de la llamada a **Update** para `AddNew`, la llamada a **Update** para **Edit** compara los valores actualizados con valores almacenados previamente en lugar de utilizar **PSEUDO\_NULL**.  La diferencia consiste en que `AddNew` no tiene valores almacenados previamente para efectuar comparaciones.  
  
3.  Se establecen directamente los valores de los miembros de datos de campo cuyos valores se desea editar o llenar para formar un nuevo registro.  Esto puede incluir llamar a `SetFieldNull`.  
  
4.  Una llamada a [Update](../Topic/CRecordset::Update.md) comprueba si hay miembros de datos de campo modificados, como se describe en el paso 2 \(vea la tabla [Secuencia de operaciones RFX durante el desplazamiento](#_core_sequence_of_rfx_operations_during_scrolling)\).  Si no ha cambiado ninguno, **Update** devuelve 0.  Si ha cambiado algún miembro de datos de campo, **Update** prepara y ejecuta una instrucción SQL **INSERT** que contiene valores para todos los campos actualizados del registro.  
  
5.  Para `AddNew`, **Update** termina restaurando los valores previamente almacenados del registro considerado como actual antes de la llamada a `AddNew`.  Para **Edit**, los valores nuevos y modificados continúan tal y como están.  
  
 La tabla siguiente muestra la secuencia de operaciones RFX que tienen lugar al agregar un nuevo registro o editar un registro existente.  
  
### Secuencia de operaciones RFX durante una operación AddNew y Edit  
  
|Operación|Operación DoFieldExchange|Operación de base de datos\/SQL|  
|---------------|-------------------------------|-------------------------------------|  
|1.  Llamar a `AddNew` o **Edit**.|||  
||2.  Realizar una copia de seguridad del búfer de edición.||  
||3.  Para `AddNew`, marcar los miembros de datos de campo como "limpios" \(sin cambios\) y Null.||  
|4.  Asignar valores a los miembros de datos de campo del conjunto de registros.|||  
|5.  Llamar a **Update**.|||  
||6.  Comprobar si hay campos modificados.||  
||7.  Compilar una instrucción SQL **INSERT** para `AddNew` o una instrucción **UPDATE** para **Edit**.||  
|||8.  Enviar el código SQL.|  
||9.  Para `AddNew`, restaurar el búfer de edición con el contenido de la copia de seguridad.  Para **Edit**, eliminar la copia de seguridad.||  
  
### RFX: eliminar registros existentes  
 Al eliminar un registro, RFX establece todos los campos en **NULL** como recordatorio de que se eliminó el registro y se debe salir de la posición que ocupa.  No es necesario disponer de más información de secuencias RFX.  
  
## Vea también  
 [Intercambio de campos de registros \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)   
 [Consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [Macros, funciones globales y variables globales](../Topic/Macros,%20Global%20Functions,%20and%20Global%20Variables.md)   
 [CFieldExchange Class](../../mfc/reference/cfieldexchange-class.md)   
 [CRecordset::DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md)