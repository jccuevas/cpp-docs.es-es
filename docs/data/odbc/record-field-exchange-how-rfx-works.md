---
title: 'Intercambio de campos de registros: Funcionamiento de RFX | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record editing [C++], using RFX
- RFX (ODBC) [C++], updating data in recordsets
- scrolling [C++]
- ODBC [C++], RFX
- data binding [C++], DFX
- scrolling [C++], RFX
- RFX (ODBC) [C++], binding fields and parameters
ms.assetid: e647cacd-62b0-4b80-9e20-b392deca5a88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 48cece77101a14efb827e48b53be2f5852df83ee
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="record-field-exchange-how-rfx-works"></a>Intercambio de campos de registros: Funcionamiento de RFX
Este tema explica el proceso RFX. Avanzada cobertura de tema:  
  
-   [RFX y el conjunto de registros](#_core_rfx_and_the_recordset)  
  
-   [El proceso RFX](#_core_the_record_field_exchange_process)  
  
> [!NOTE]
>  En este tema se aplica a las clases derivadas de `CRecordset` qué masiva de filas no se ha implementado la obtención. Si se utiliza la obtención masiva de filas, se implementa el intercambio masivo de campos de registros (RFX masivo). RFX masivo es similar a RFX. Para entender las diferencias, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_rfx_and_the_recordset"></a> RFX y el conjunto de registros  
 Los miembros de datos de campo del objeto de conjunto de registros, tomados en conjunto, constituyen un búfer de edición que contiene las columnas seleccionadas de un registro. Cuando el conjunto de registros se abre por primera vez y está a punto de leer el primer registro, RFX enlaza (asocia) cada una de las columnas seleccionadas a la dirección del miembro de datos de campo correspondiente. Cuando el conjunto de registros actualiza un registro, RFX llama a funciones de la API de ODBC para enviar una instancia de SQL **actualización** o **insertar** instrucción del controlador. RFX utiliza su conocimiento de los miembros de datos de campo para especificar las columnas que se va a escribir.  
  
 El marco de trabajo realiza una copia del búfer de edición en determinadas fases para poder restaurar su contenido si es necesario. RFX hace una copia de seguridad del búfer de edición antes de agregar un nuevo registro y antes de editar un registro existente. Restaura el búfer de edición en algunos casos, por ejemplo, después de un **actualización** siguiente llamada `AddNew`. El búfer de edición no se restaura si se deja un búfer recién modificado desplazándose, por ejemplo, mover a otro registro antes de llamar a **actualización**.  
  
 Además de intercambiar datos entre el origen de datos y los miembros de datos de campo del conjunto de registros, RFX administra los parámetros de enlace. Cuando se abre el conjunto de registros, los miembros de datos de parámetro se enlazan en el orden de la "?" marcadores de posición en la instrucción SQL que `CRecordset::Open` construye. Para obtener más información, consulte [conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
 La invalidación de la clase de conjunto de registros `DoFieldExchange` hace todo el trabajo, moviendo los datos en ambas direcciones. Al igual que el intercambio de datos de cuadros de diálogo (DDX), RFX necesita información sobre los miembros de datos de la clase. El asistente proporciona la información necesaria escribiendo una implementación específica del conjunto de registros de `DoFieldExchange` para usted, en función de los datos del campo miembro nombres y tipos de datos especificados mediante el asistente.  
  
##  <a name="_core_the_record_field_exchange_process"></a> Proceso de intercambio de campos de registro  
 Esta sección describe la secuencia de eventos RFX tal como un objeto de conjunto de registros está abierto y agregar, actualizar y eliminar registros. La tabla [secuencia de RFX operaciones durante el conjunto de registros abierto](#_core_sequence_of_rfx_operations_during_recordset_open) y la tabla [secuencia de operaciones RFX durante el desplazamiento](#_core_sequence_of_rfx_operations_during_scrolling) en este tema se muestra el proceso como procesos RFX un **mover**comando en el conjunto de registros y administra una actualización. Durante estos procesos, [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) se llama para realizar varias operaciones diferentes. El **m_nOperation** miembro de datos de la [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objeto determina qué operación se solicita. Le resultará útil leer [conjunto de registros: cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) y [conjunto de registros: actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) antes de leer este material.  
  
###  <a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a> RFX: Enlace inicial de columnas y parámetros  
 Se producen las siguientes actividades RFX, en el orden mostrado, cuando se llama a un objeto de conjunto de registros [abiertos](../../mfc/reference/crecordset-class.md#open) función miembro:  
  
-   Si el conjunto de registros tiene miembros de datos de parámetro, el marco llama a `DoFieldExchange` para enlazar los parámetros con marcadores de posición de parámetro de cadena de la instrucción SQL del conjunto de registros. Una representación, dependiente del tipo del valor del parámetro se utiliza para cada marcador de posición de datos se encuentran en la **seleccione** instrucción. Esto se produce después de prepara la instrucción SQL, pero antes de que se ejecute. Para obtener información acerca de la preparación de instrucciones, consulte la **:: SQLPrepare** función en el archivo ODBC *referencia del programador de*.  
  
-   Las llamadas de framework `DoFieldExchange` una segunda vez para enlazar los valores de las columnas seleccionadas con los miembros de datos correspondientes en el conjunto de registros. Esto establece el objeto de conjunto de registros como búfer de edición que contiene las columnas de la primera entrada.  
  
-   El conjunto de registros ejecuta la instrucción SQL y el origen de datos selecciona el primer registro. Las columnas del registro se cargan en los miembros de datos de campo del conjunto de registros.  
  
 En la tabla siguiente se muestra la secuencia de operaciones RFX al abrir un conjunto de registros.  
  
### <a name="_core_sequence_of_rfx_operations_during_recordset_open"></a> Secuencia de operaciones RFX durante la apertura de conjunto de registros  
  
|La operación|Operación DoFieldExchange|Operación de base de datos/SQL|  
|--------------------|-------------------------------|-----------------------------|  
|1. Abra el conjunto de registros.|||  
||2. Generar una instrucción SQL.||  
|||3. Enviar el código SQL.|  
||4. Enlazar a miembros de datos de parámetro.||  
||5. Enlazar a miembros de datos de campo a las columnas.||  
|||6. ODBC realiza el traslado y rellena los datos.|  
||7. Corregir los datos de C++.||  
  
 Conjuntos de registros usan la ejecución preparada de ODBC para permitir volver a consultar rápido con la misma instrucción SQL. Para obtener más información sobre la ejecución preparada, vea el SDK de ODBC *referencia del programador* en MSDN Library.  
  
###  <a name="_mfc_rfx.3a_.scrolling"></a> RFX: desplazamiento  
 Cuando se desplaza de un registro a otro, el marco llama a `DoFieldExchange` para reemplazar los valores almacenados previamente en los miembros de datos de campo con los valores para el nuevo registro.  
  
 En la tabla siguiente se muestra la secuencia de operaciones RFX cuando el usuario se mueve de un registro a otro.  
  
### <a name="_core_sequence_of_rfx_operations_during_scrolling"></a> Secuencia de operaciones RFX durante el desplazamiento  
  
|La operación|Operación DoFieldExchange|Operación de base de datos/SQL|  
|--------------------|-------------------------------|-----------------------------|  
|1. Llame a `MoveNext` o una de las demás funciones Move.|||  
|||2. ODBC realiza el traslado y rellena los datos.|  
||3. Corregir los datos de C++.||  
  
###  <a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a> RFX: Agregar nuevos registros y editar los registros existentes  
 Si agrega un nuevo registro, el conjunto de registros funciona como un búfer de edición para generar el contenido del nuevo registro. Al igual que con la adición de registros, editar registros implica cambiar los valores de los miembros de datos de campo del conjunto de registros. Desde la perspectiva RFX, la secuencia es como sigue:  
  
1.  La llamada para el conjunto de registros [AddNew](../../mfc/reference/crecordset-class.md#addnew) o [editar](../../mfc/reference/crecordset-class.md#edit) función miembro hace que RFX almacene el búfer de edición actual para que pueda restaurarse más tarde.  
  
2.  `AddNew` o **editar** prepara los campos en el búfer de edición para que RFX pueda detectar los miembros de datos de campo modificados.  
  
     Dado que un nuevo registro no tiene ningún valor anterior al comparar los nuevos, `AddNew` establece el valor de cada miembro de datos de campo a un **PSEUDO_NULL** valor. Posteriormente, cuando se llama a **actualización**, RFX compara el valor de cada miembro de datos con la **PSEUDO_NULL** valor. Si hay una diferencia, el miembro de datos se ha configurado. (**PSEUDO_NULL** no es el mismo que una columna de registro con un valor Null es true ni ninguno de ellos mismos como C++ **NULL**.)  
  
     A diferencia de la **actualización** llamar para `AddNew`, el **actualización** llamar para **editar** compara los valores actualizados con valores almacenados previamente en lugar de usar **PSEUDO_NULL**. La diferencia es que `AddNew` no tiene ningún valor almacenado previamente para la comparación.  
  
3.  Establecer directamente los valores de los miembros de datos de campo cuyos valores desea editar o que desea rellenar para un nuevo registro. Esto puede incluir llamar a `SetFieldNull`.  
  
4.  La llamada a [actualización](../../mfc/reference/crecordset-class.md#update) busca los miembros de datos de campo modificados, como se describe en el paso 2 (vea la tabla [secuencia de operaciones RFX durante el desplazamiento](#_core_sequence_of_rfx_operations_during_scrolling)). Si no ha cambiado ninguno, **actualización** devuelve 0. Si han cambiado algunos miembros de datos de campo, **actualización** prepara y ejecuta una instancia de SQL **insertar** instrucción que contiene valores para todos los campos actualizados en el registro.  
  
5.  Para `AddNew`, **actualización** termina restaurando los valores previamente almacenados del registro que era el actual antes de la `AddNew` llamar. Para **editar**, los valores nuevos y modificados permanecen en su lugar.  
  
 En la tabla siguiente se muestra la secuencia de operaciones RFX al agregar un nuevo registro o editar un registro existente.  
  
### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>Secuencia de operaciones RFX durante AddNew y Edit  
  
|La operación|Operación DoFieldExchange|Operación de base de datos/SQL|  
|--------------------|-------------------------------|-----------------------------|  
|1. Llame a `AddNew` o **editar**.|||  
||2. Hacer copia de seguridad del búfer de edición.||  
||3. Para `AddNew`, marcar los miembros de datos de campo como "limpia" y Null.||  
|4. Asignar valores a los miembros de datos de campo de conjunto de registros.|||  
|5. Llame a **actualización**.|||  
||6. Compruebe si hay campos modificados.||  
||7. Generar SQL **insertar** instrucción para `AddNew` o **actualización** instrucción para **editar**.||  
|||8. Enviar el código SQL.|  
||9. Para `AddNew`, restaurar el búfer de edición con el contenido de la copia de seguridad. Para **editar**, elimine la copia de seguridad.||  
  
### <a name="rfx-deleting-existing-records"></a>RFX: Eliminar registros existentes  
 Cuando se elimina un registro, RFX establece todos los campos en **NULL** como recordatorio de que el registro se elimina y debe salir de él. No es necesario cualquier otra información de secuencia RFX.  
  
## <a name="see-also"></a>Vea también  
 [Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)   
 [Consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [Macros, funciones globales y Variables globales](../../mfc/reference/mfc-macros-and-globals.md)  
 [Clase CFieldExchange](../../mfc/reference/cfieldexchange-class.md)   
 [CRecordset:: DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)