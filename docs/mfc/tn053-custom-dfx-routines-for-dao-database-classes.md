---
title: 'TN053: Personalizar las rutinas DFX para las clases de base de datos DAO'
ms.date: 09/17/2019
helpviewer_keywords:
- MFC, DAO and
- database classes [MFC], DAO
- DAO [MFC], MFC
- DFX (DAO record field exchange) [MFC], custom routines
- TN053
- DAO [MFC], classes
- DFX (DAO record field exchange) [MFC]
- custom DFX routines [MFC]
ms.assetid: fdcf3c51-4fa8-4517-9222-58aaa4f25cac
ms.openlocfilehash: f7ad854f4dbb4e90c09e886c69260e4e2eea3be2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365260"
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>TN053: Personalizar las rutinas DFX para las clases de base de datos DAO

> [!NOTE]
> DAO se usa con bases de datos de Access y se admite a través de Office 2013. DAO 3.6 es la versión final, y se considera obsoleto. El entorno y los asistentes de Visual C++ no admiten DAO (aunque las clases DAO están incluidas y todavía puede usarlas). Microsoft recomienda usar [plantillas OLE DB](../data/oledb/ole-db-templates.md) u ODBC y [MFC](../data/odbc/odbc-and-mfc.md) para nuevos proyectos. Solo debe usar DAO para mantener las aplicaciones existentes.

Esta nota técnica describe el mecanismo de intercambio de campos de registros DAO (DFX). Para ayudar a entender lo que está `DFX_Text` sucediendo en las rutinas DFX, la función se explicará en detalle como un ejemplo. Como fuente adicional de información para esta nota técnica, puede examinar el código para el otro de las funciones DFX individuales. Probablemente no necesitará una rutina DFX personalizada tan a menudo como necesite una rutina RFX personalizada (utilizada con clases de base de datos ODBC).

Esta nota técnica contiene:

- Descripción general de DFX

- [Ejemplos](#_mfcnotes_tn053_examples) de uso de DAO Record Field Exchange y Dynamic Binding

- [Cómo funciona DFX](#_mfcnotes_tn053_how_dfx_works)

- [Qué hace su rutina DFX personalizada](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)

- [Detalles de DFX_Text](#_mfcnotes_tn053_details_of_dfx_text)

**Descripción general de DFX**

El mecanismo de intercambio de campos de registros DAO (DFX) se `CDaoRecordset` utiliza para simplificar el procedimiento de recuperación y actualización de datos cuando se usa la clase. El proceso se simplifica mediante `CDaoRecordset` los miembros de datos de la clase. Derivando de `CDaoRecordset`, puede agregar miembros de datos a la clase derivada que representa cada campo de una tabla o consulta. Este mecanismo de "enlace estático" es simple, pero puede que no sea el método de recuperación/actualización de datos de elección para todas las aplicaciones. DFX recupera todos los campos enlazados cada vez que se cambia el registro actual. Si está desarrollando una aplicación sensible al rendimiento que no requiere recuperar todos `CDaoRecordset::GetFieldValue` los `CDaoRecordset::SetFieldValue` campos cuando se cambia la moneda, "enlace dinámico" a través de y puede ser el método de acceso a datos de elección.

> [!NOTE]
> DFX y el enlace dinámico no son mutuamente excluyentes, por lo que se puede usar un uso híbrido de enlace estático y dinámico.

## <a name="example-1--use-of-dao-record-field-exchange-only"></a><a name="_mfcnotes_tn053_examples"></a>Ejemplo 1 — Uso de DAO Record Field Exchange solamente

(supone `CDaoRecordset` — clase `CMySet` derivada ya abierta)

```
// Add a new record to the customers table
myset.AddNew();

myset.m_strCustID = _T("MSFT");

myset.m_strCustName = _T("Microsoft");

myset.Update();
```

**Ejemplo 2 — Uso de enlace dinámico solamente**

(supone usar `CDaoRecordset` la `rs`clase, , y ya está abierta)

```
// Add a new record to the customers table
COleVariant  varFieldValue1 (_T("MSFT"),
    VT_BSTRT);

//Note: VT_BSTRT flags string type as ANSI,
    instead of UNICODE default
COleVariant  varFieldValue2  (_T("Microsoft"),
    VT_BSTRT);

rs.AddNew();

rs.SetFieldValue(_T("Customer_ID"),
    varFieldValue1);

rs.SetFieldValue(_T("Customer_Name"),
    varFieldValue2);

rs.Update();
```

**Ejemplo 3 — Uso de DAO Record Field Exchange y enlace dinámico**

(supone que se `CDaoRecordset`examinan los `emp`datos de los empleados con la clase derivada )

```
// Get the employee's data so that it can be displayed
emp.MoveNext();

// If user wants to see employee's photograph,
// fetch it
COleVariant varPhoto;
if (bSeePicture)
    emp.GetFieldValue(_T("photo"),
    varPhoto);

// Display the data
PopUpEmployeeData(emp.m_strFirstName,
    emp.m_strLastName,
    varPhoto);
```

## <a name="how-dfx-works"></a><a name="_mfcnotes_tn053_how_dfx_works"></a>Cómo funciona DFX

El mecanismo DFX funciona de forma similar al mecanismo de intercambio de campos de registros (RFX) utilizado por las clases ODBC de MFC. Los principios de DFX y RFX son los mismos, pero hay numerosas diferencias internas. El diseño de las funciones DFX era tal que prácticamente todo el código es compartido por las rutinas DFX individuales. En el nivel más alto DFX sólo hace algunas cosas.

- DFX construye la cláusula **SELECT** de SQL y la cláusula SQL **PARAMETERS** si es necesario.

- DFX construye la estructura de enlace `GetRows` utilizada por la función de DAO (más sobre esto más adelante).

- DFX administra el búfer de datos utilizado para detectar campos sucios (si se utiliza el almacenamiento en búfer doble)

- DFX administra las matrices de estado **NULL** y **DIRTY** y establece valores si es necesario en las actualizaciones.

En el corazón del mecanismo `CDaoRecordset` DFX está `DoFieldExchange` la función de la clase derivada. Esta función distribuye llamadas a las funciones DFX individuales de un tipo de operación adecuado. Antes `DoFieldExchange` de llamar a las funciones MFC internas establezca el tipo de operación. La lista siguiente muestra los distintos tipos de operación y una breve descripción.

|Operación|Descripción|
|---------------|-----------------|
|`AddToParameterList`|Construye cláusula PARAMETERS|
|`AddToSelectList`|Crea cláusula SELECT|
|`BindField`|Configura la estructura de encuadernación|
|`BindParam`|Establece los valores de los parámetros|
|`Fixup`|Establece el estado NULL|
|`AllocCache`|Asigna caché para la comprobación sucia|
|`StoreField`|Guarda el registro actual en la memoria caché|
|`LoadField`|Restaura la memoria caché a los valores de los miembros|
|`FreeCache`|Libera caché|
|`SetFieldNull`|Establece el estado del campo & valor en NULL|
|`MarkForAddNew`|Marcas de campos sucios si no PSEUDO NULL|
|`MarkForEdit`|Marca los campos sucios si no coinciden con la caché|
|`SetDirtyField`|Establece los valores de campo marcados como sucios|

En la siguiente sección, cada operación se `DFX_Text`explicará con más detalle para .

La característica más importante para entender sobre el proceso `GetRows` de intercambio `CDaoRecordset` de campos de registros DAO es que utiliza la función del objeto. La `GetRows` función DAO puede funcionar de varias maneras. Esta nota técnica sólo `GetRows` describirá brevemente, ya que está fuera del alcance de esta nota técnica.
DAO `GetRows` puede funcionar de varias maneras.

- Puede capturar varios registros y varios campos de datos a la vez. Esto permite un acceso más rápido a los datos con la complicación de tratar con una estructura de datos grande y los desplazamientos adecuados para cada campo y para cada registro de datos en la estructura. MFC no aprovecha este mecanismo de obtención de registros múltiples.

- Otra `GetRows` forma de trabajar es permitir que los programadores especifiquen direcciones de enlace para los datos recuperados de cada campo para un registro de datos.

- DAO también "volverá a llamar" en el llamador para las columnas de longitud variable para permitir que el autor de la llamada asigne memoria. Esta segunda característica tiene la ventaja de minimizar el número de copias de datos, así `CDaoRecordset` como permitir el almacenamiento directo de datos en miembros de una clase (la clase derivada). Este segundo mecanismo es el método MFC `CDaoRecordset` utiliza para enlazar a los miembros de datos en clases derivadas.

## <a name="what-your-custom-dfx-routine-does"></a><a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a>Qué hace su rutina DFX personalizada

De esta discusión se desprende que la operación más importante implementada en cualquier función DFX `GetRows`debe ser la capacidad de configurar las estructuras de datos necesarias para llamar correctamente. Hay un número de otras operaciones que una función DFX debe admitir también, `GetRows` pero ninguna tan importante o compleja como la preparación correcta para la llamada.

El uso de DFX se describe en la documentación en línea. Esencialmente, hay dos requisitos. En primer lugar, los `CDaoRecordset` miembros deben agregarse a la clase derivada para cada campo y parámetro enlazado. Después `CDaoRecordset::DoFieldExchange` de esto debe ser anulado. Tenga en cuenta que el tipo de datos del miembro es importante. Debe coincidir con los datos del campo de la base de datos o al menos ser convertible a ese tipo. Por ejemplo, un campo numérico en la base de datos, como `CString` un entero largo, siempre se puede convertir en texto y enlazar a un miembro, pero un campo de texto en una base de datos no necesariamente se puede convertir en una representación numérica, como entero largo y enlazado a un miembro entero largo. DAO y el motor de base de datos Microsoft Jet son responsables de la conversión (en lugar de MFC).

## <a name="details-of-dfx_text"></a><a name="_mfcnotes_tn053_details_of_dfx_text"></a>Detalles de DFX_Text

Como se mencionó anteriormente, la mejor manera de explicar cómo funciona DFX es trabajar a través de un ejemplo. Para este propósito pasar por `DFX_Text` los internos de debe funcionar bastante bien para ayudar a proporcionar al menos una comprensión básica de DFX.

- `AddToParameterList`

   Esta operación compila **PARAMETERS** la`Parameters <param name>, <param type> ... ;`cláusula SQL PARAMETERS (" ") requerida por Jet. Cada parámetro se denomina y se escribe (como se especifica en la llamada RFX). Consulte la `CDaoFieldExchange::AppendParamType` función de función para ver los nombres de los tipos individuales. En el `DFX_Text`caso de , el tipo utilizado es **texto**.

- `AddToSelectList`

   Crea la cláusula **SELECT** de SQL. Esto es bastante sencillo, ya que el nombre de columna`SELECT <column name>, ...`especificado por la llamada DFX simplemente se anexa (" ").

- `BindField`

   La más compleja de las operaciones. Como se mencionó anteriormente, aquí `GetRows` es donde se configura la estructura de enlace DAO utilizada por. Como se puede ver `DFX_Text` en el código en los tipos de información en la `DFX_Text`estructura incluyen el tipo DAO utilizado (**DAO_CHAR** o **DAO_WCHAR** en el caso de ). Además, también se configura el tipo de enlace utilizado. En una sección `GetRows` anterior se describió sólo brevemente, pero era suficiente para explicar que el tipo de enlace utilizado por MFC siempre es enlace de dirección directa (**DAOBINDING_DIRECT**). Además para el enlace `DFX_Text`de columna de longitud variable (como ) se utiliza el enlace de devolución de llamada para que MFC pueda controlar la asignación de memoria y especificar una dirección de la longitud correcta. Esto significa que MFC siempre puede indicar a DAO "dónde" colocar los datos, lo que permite enlazar directamente a las variables miembro. El resto de la estructura de enlace se rellena con elementos como la dirección de la función de devolución de llamada de asignación de memoria y el tipo de enlace de columna (enlace por nombre de columna).

- `BindParam`

   Se trata de una `SetParamValue` operación sencilla que llama con el valor de parámetro especificado en el miembro de parámetro.

- `Fixup`

   Rellena el estado **NULL** para cada campo.

- `SetFieldNull`

   Esta operación solo marca cada estado de campo como **NULL** y establece el valor de la variable miembro **en PSEUDO_NULL**.

- `SetDirtyField`

   Llamadas `SetFieldValue` para cada campo marcado sucio.

Todas las operaciones restantes solo se ocupan del uso de la memoria caché de datos. La caché de datos es un búfer adicional de los datos del registro actual que se utiliza para facilitar determinadas cosas. Por ejemplo, los campos "sucios" se pueden detectar automáticamente. Como se describe en la documentación en línea se puede desactivar por completo o a nivel de campo. La implementación del búfer utiliza un mapa. Este mapa se utiliza para hacer coincidir las copias asignadas dinámicamente de `CDaoRecordset` los datos con la dirección del campo "enlazado" (o miembro de datos derivado).

- `AllocCache`

   Asigna dinámicamente el valor del campo almacenado en caché y lo agrega al mapa.

- `FreeCache`

   Elimina el valor del campo almacenado en caché y lo elimina del mapa.

- `StoreField`

   Copia el valor del campo actual en la caché de datos.

- `LoadField`

   Copia el valor almacenado en caché en el miembro de campo.

- `MarkForAddNew`

   Comprueba si el valor del campo actual no es**NULL** y lo marca sucio si es necesario.

- `MarkForEdit`

   Compara el valor del campo actual con la caché de datos y las marcas sucias si es necesario.

> [!TIP]
> Modele las rutinas DFX personalizadas en las rutinas DFX existentes para tipos de datos estándar.

## <a name="see-also"></a>Consulte también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
