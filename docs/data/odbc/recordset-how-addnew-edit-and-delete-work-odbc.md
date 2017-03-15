---
title: "Conjunto de registros: Funcionamiento de AddNew, Edit y Delete (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddNew (método)"
  - "datos en conjuntos de registros [C++]"
  - "conjuntos de registros ODBC [C++], agregar registros"
  - "conjuntos de registros ODBC [C++], eliminar registros"
  - "conjuntos de registros ODBC [C++], editar registros"
  - "edición de registros [C++], en conjuntos de registros"
  - "registros [C++], agregar"
  - "registros [C++], eliminar en conjuntos de registros"
  - "registros [C++], editar"
  - "registros [C++], actualizar"
  - "conjuntos de registros [C++], agregar registros"
  - "conjuntos de registros [C++], eliminar registros"
  - "conjuntos de registros [C++], editar registros"
  - "conjuntos de registros [C++], actualizar"
ms.assetid: cab43d43-235a-4bed-ac05-67d10e94f34e
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Conjunto de registros: Funcionamiento de AddNew, Edit y Delete (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema es aplicable a las clases ODBC de MFC.  
  
 Este tema explica el funcionamiento de las funciones miembro `AddNew`, **Edit** y **Delete** de la clase `CRecordset`.  Entre los temas tratados, se incluyen los siguientes:  
  
-   [Funcionamiento de la adición de registros](#_core_adding_a_record)  
  
-   [Visibilidad de los registros agregados](#_core_visibility_of_added_records)  
  
-   [Funcionamiento de la edición de registros](#_core_editing_an_existing_record)  
  
-   [Funcionamiento de la eliminación de registros](#_core_deleting_a_record)  
  
> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas.  Si utiliza la obtención masiva de filas, vea [Conjunto de registros: Obtener registros de forma masiva \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Como complemento, puede resultar conveniente leer [Intercambio de campos de registros: Funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md), que describe el rol correspondiente de RFX en las operaciones de actualización.  
  
##  <a name="_core_adding_a_record"></a> Agregar un registro  
 Agregar un nuevo registro implica llamar a la función miembro [AddNew](../Topic/CRecordset::AddNew.md) del conjunto de registros, establecer los valores de los miembros de datos de campo del nuevo registro y llamar a la función miembro [Update](../Topic/CRecordset::Update.md) para guardar el registro en el origen de datos.  
  
 Como condición previa para llamar a `AddNew`, no se debe abrir el conjunto de registros como sólo lectura.  Las funciones miembro `CanUpdate` y `CanAppend` permiten determinar estas condiciones.  
  
 Cuando se llama a `AddNew`:  
  
-   Se almacena el registro en el búfer de edición para que pueda restaurarse el contenido si se cancela la operación.  
  
-   Se marcan los miembros de datos de campo para que sea posible detectar cambios en ellos con posterioridad.  También se marcan como limpios \(sin cambios\) y se establecen en Null.  
  
 Después de llamar a `AddNew`, el búfer de edición representa un registro nuevo y vacío, listo para llenarlo de valores.  Para ello, establezca manualmente los valores.  En lugar de especificar un valor de datos real para un campo, se puede llamar a `SetFieldNull` y especificar el valor Null.  
  
 Para confirmar los cambios, llame a **Update**.  Al llamar a **Update** para el nuevo registro:  
  
-   Si el controlador ODBC admite la función de la API ODBC **::SQLSetPos**, MFC usa la función para agregar el registro al origen de datos.  Con **::SQLSetPos**, MFC puede agregar un registro más eficientemente, ya que no es necesario crear ni procesar ninguna instrucción SQL.  
  
-   Si no se puede usar **::SQLSetPos**, MFC hace lo siguiente:  
  
    1.  Si no se detectan cambios, **Update** no hace nada y devuelve 0.  
  
    2.  Si hay cambios, **Update** crea una instrucción SQL **INSERT**.  Las columnas representadas por todos los miembros de datos de campo con modificaciones se enumeran en la instrucción **INSERT**.  Para forzar la inclusión de una columna, llame a la función miembro [SetFieldDirty](../Topic/CRecordset::SetFieldDirty.md):  
  
        ```  
        SetFieldDirty( &m_dataMember, TRUE );  
        ```  
  
    3.  **Update** confirma el nuevo registro: la instrucción **INSERT** se ejecuta y el registro se confirma en la tabla del origen de datos \(y del conjunto de registros, si no es una instantánea\) a menos que haya una transacción en curso.  
  
    4.  El registro almacenado se restaura en el búfer de edición.  El registro que era el actual antes de la llamada a `AddNew` recupera su condición de registro actual, sin importar si se ejecutó con éxito la instrucción **INSERT**.  
  
    > [!TIP]
    >  Para obtener un control completo de los nuevos registros, adopte el siguiente enfoque: establezca los valores de cualquier campo que vaya a contener valores y, a continuación, establezca explícitamente cualquier campo que permanezca como Null llamando a `SetFieldNull` con un puntero al campo y el parámetro **TRUE** \(el predeterminado\).  Si desea garantizar que no se guarde un campo en el origen de datos, llame a `SetFieldDirty` con un puntero al campo y el parámetro **FALSE**, y no modifique el valor del campo.  Para determinar si se permite el valor Null para un campo, llame a `IsFieldNullable`.  
  
    > [!TIP]
    >  Para detectar cuándo cambian de valor los miembros de datos de un conjunto de registros, MFC utiliza un valor **PSEUDO\_NULL** apropiado a cada tipo de datos que se puede almacenar en un conjunto de registros.  Si es necesario establecer un campo en el valor **PSEUDO\_NULL** y el campo parece estar ya marcado como Null, también se debe llamar a `SetFieldNull`, pasando la dirección del campo en el primer parámetro y **FALSE** en el segundo.  
  
##  <a name="_core_visibility_of_added_records"></a> Visibilidad de los registros agregados  
 ¿Cuándo es visible un registro agregado para el conjunto de registros?  Los registros agregados a veces aparecen visibles y a veces no, dependiendo de dos factores:  
  
-   La capacidad del controlador.  
  
-   Qué es capaz de aprovechar el marco de trabajo.  
  
 Si el controlador ODBC admite la función de la API ODBC **::SQLSetPos**, MFC usa la función para agregar registros.  Con **::SQLSetPos**, los registros agregados son visibles para cualquier conjunto de registros MFC actualizable.  Sin compatibilidad con esta función, los registros agregados no se ven y se debe llamar a **Requery** para verlos.  El uso de **::SQLSetPos** es también más eficiente.  
  
##  <a name="_core_editing_an_existing_record"></a> Editar un registro existente  
 Editar un registro existente en un conjunto de registros implica desplazarse al registro, llamar a la función miembro [Edit](../Topic/CRecordset::Edit.md) del conjunto de registros, establecer los valores de los miembros de datos de campo del nuevo registro y llamar a la función miembro [Update](../Topic/CRecordset::Update.md) para guardar el registro modificado en el origen de datos.  
  
 Como condición previa para llamar a **Edit**, el conjunto de registros debe ser actualizable y hallarse en un registro.  Las funciones miembro `CanUpdate` e `IsDeleted` permiten determinar estas condiciones.  Asimismo, el registro actual no puede haber sido eliminado todavía, y debe haber registros en el conjunto de registros \(tanto `IsBOF` como `IsEOF` devuelven 0\).  
  
 Cuando se llama a **Edit**, se almacena el registro del búfer de edición \(el registro actual\).  Los valores del registro almacenado se usan más tarde para detectar si se modificó algún campo.  
  
 Después de llamar a **Edit**, el búfer de edición continúa representando al registro actual, pero ahora está listo para aceptar campos en los miembros de datos de campo.  Para cambiar el registro, deben establecerse manualmente los valores de cualquier miembro de datos de campo que se desee editar.  En lugar de especificar un valor de datos real para un campo, se puede llamar a `SetFieldNull` y especificar el valor Null.  Para confirmar los cambios, llame a **Update**.  
  
> [!TIP]
>  Para salir del modo `AddNew` o **Edit**, llame a **Move** con el parámetro **AFX\_MOVE\_REFRESH**.  
  
 Como condición previa para llamar a **Update**, el conjunto de registros no debe estar vacío y no se debe haber eliminado el registro actual.  `IsBOF`, `IsEOF` y `IsDeleted` deben devolver 0.  
  
 Al llamar a **Update** para el registro editado:  
  
-   Si el controlador ODBC admite la función de la API ODBC **::SQLSetPos**, MFC usa la función para actualizar el registro en el origen de datos.  Con **::SQLSetPos**, el controlador compara el búfer de edición con el registro correspondiente en el servidor, actualizando este último si son diferentes.  Con **::SQLSetPos**, MFC puede actualizar un registro más eficientemente, ya que no es necesario crear ni procesar ninguna instrucción SQL.  
  
     O bien  
  
-   Si no se puede usar **::SQLSetPos**, MFC hace lo siguiente:  
  
    1.  Si no hubo cambios, **Update** no hace nada y devuelve 0.  
  
    2.  Si hay cambios, **Update** crea una instrucción SQL **UPDATE**.  Las columnas enumeradas en la instrucción **UPDATE** se basan en los miembros de datos de campo que han cambiado.  
  
    3.  **Update** confirma los cambios \(ejecuta la instrucción **UPDATE**\) y se modifica el registro en el origen de datos, pero no se confirma el cambio si hay una transacción en progreso \(vea [Transacción: Realizar una transacción en un conjunto de registros \(ODBC\)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md) para obtener información sobre cómo afecta la transacción a la actualización\).  ODBC conserva una copia del registro que también cambia.  
  
    4.  A diferencia del proceso que sigue `AddNew`, **Edit no restaura el registro almacenado.** El registro editado permanece en su ubicación como registro actual.  
  
    > [!CAUTION]
    >  Al prepararse para actualizar un conjunto de registros llamando a **Update**, asegúrese de que incluye todas las columnas que componen la clave principal de la tabla \(o todas las columnas que componen cualquiera de los índices únicos de la tabla, o suficientes columnas para identificar la fila de forma única\).  En algunos casos, el marco de trabajo sólo puede utilizar las columnas seleccionadas en el conjunto de registros para identificar qué registro de la tabla se actualiza.  Sin disponer de todas las columnas necesarias, se pueden actualizar varios registros de la tabla.  En este caso, el marco de trabajo produce excepciones al llamar a **Update**.  
  
    > [!TIP]
    >  Si se llama a `AddNew` o **Edit** después de haber llamado a cada función con anterioridad pero antes de llamar a **Update**, el búfer de edición se actualiza con el registro almacenado, reemplazando el registro nuevo o editado en proceso.  Este comportamiento proporciona una forma de anular una operación `AddNew` o **Edit** y comenzar una nueva: si se determina que el registro en proceso presenta errores, basta con llamar a `AddNew` o **Edit** de nuevo.  
  
##  <a name="_core_deleting_a_record"></a> Eliminar un registro  
 La eliminación de un registro de un conjunto de registros implica desplazarse al registro y llamar a la función miembro [Delete](../Topic/CRecordset::Delete.md) del conjunto de registros.  A diferencia de `AddNew` y **Edit**, **Delete** no requiere una llamada similar a **Update**.  
  
 Como condición previa para llamar a **Delete**, el conjunto de registros debe ser actualizable y hallarse en un registro.  Las funciones miembro `CanUpdate`, `IsBOF`, `IsEOF` e `IsDeleted` permiten determinar estas condiciones.  
  
 Cuando se llama a **Delete**:  
  
-   Si el controlador ODBC admite la función de la API ODBC **::SQLSetPos**, MFC usa la función para eliminar el registro en el origen de datos.  Usar **::SQLSetPos** suele ser más eficiente que usar SQL.  
  
     O bien  
  
-   Si no se puede usar **::SQLSetPos**, MFC hace lo siguiente:  
  
    1.  No se realiza copia de seguridad del registro actual del búfer de edición, como ocurre con `AddNew` y **Edit**.  
  
    2.  **Delete** crea una instrucción SQL **DELETE** que quita el registro.  
  
         No se almacena el registro actual en el búfer de edición, como ocurre con `AddNew` y **Edit.**  
  
    3.  **Delete** confirma la eliminación, ejecutando en efecto la instrucción **DELETE**.  El registro se marca como eliminado en el origen de datos y, si es una instantánea, en ODBC.  
  
    4.  Los valores del registro eliminado continúan estando en los miembros de datos de campo del conjunto de registros, pero éstos se marcan como Null y la función miembro `IsDeleted` del conjunto de registros devuelve un valor distinto de cero.  
  
    > [!NOTE]
    >  Después de eliminar un registro, es conveniente desplazarse a otro registro para llenar el búfer de edición con los datos del nuevo registro.  Es un error llamar a **Delete** de nuevo o llamar a **Edit**.  
  
 Para obtener más información acerca de las instrucciones SQL usadas en operaciones de actualización, vea [SQL](../../data/odbc/sql.md).  
  
## Vea también  
 [Conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Información adicional sobre las actualizaciones \(ODBC\)](../../data/odbc/recordset-more-about-updates-odbc.md)   
 [Intercambio de campos de registros \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)