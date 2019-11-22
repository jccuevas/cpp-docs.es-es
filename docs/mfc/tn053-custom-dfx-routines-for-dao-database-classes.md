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
ms.openlocfilehash: 6dde96520d9472726da86f8da295770cccc5d42c
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303438"
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>TN053: Personalizar las rutinas DFX para las clases de base de datos DAO

> [!NOTE]
>  DAO se utiliza con bases de datos de Access y se admite a través de Office 2013. DAO 3,6 es la versión final y se considera obsoleta. Los asistentes C++ y el entorno visual no admiten DAO (aunque las clases DAO están incluidas y todavía se pueden utilizar). Microsoft recomienda que use [plantillas de OLE DB](../data/oledb/ole-db-templates.md) u [ODBC y MFC](../data/odbc/odbc-and-mfc.md) para proyectos nuevos. Solo se debe utilizar DAO en el mantenimiento de las aplicaciones existentes.

Esta nota técnica describe el mecanismo de intercambio de campos de registros (DFX) de DAO. Para ayudar a comprender lo que ocurre en las rutinas DFX, la función `DFX_Text` se explicará en detalle como ejemplo. Como origen adicional de la información de esta nota técnica, puede examinar el código para el resto de las funciones DFX individuales. Probablemente no necesitará una rutina DFX personalizada tantas veces como necesite una rutina de RFX personalizada (que se usa con las clases de base de datos ODBC).

Esta nota técnica contiene:

- Información general sobre DFX

- [Ejemplos](#_mfcnotes_tn053_examples) de uso del intercambio de campos de registros DAO y el enlace dinámico

- [Cómo funciona DFX](#_mfcnotes_tn053_how_dfx_works)

- [Lo que hace la rutina DFX personalizada](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)

- [Detalles de DFX_Text](#_mfcnotes_tn053_details_of_dfx_text)

**Información general sobre DFX**

El mecanismo de intercambio de campos de registros (DFX) de DAO se usa para simplificar el procedimiento de recuperación y actualización de datos cuando se usa la clase `CDaoRecordset`. El proceso se simplifica mediante el uso de miembros de datos de la clase `CDaoRecordset`. Al derivar de `CDaoRecordset`, puede Agregar miembros de datos a la clase derivada que representa cada campo de una tabla o consulta. Este mecanismo de "enlace estático" es sencillo, pero puede que no sea el método de recuperación o actualización de datos que elija para todas las aplicaciones. DFX recupera cada campo enlazado cada vez que se cambia el registro actual. Si está desarrollando una aplicación sensible al rendimiento que no requiere la captura de todos los campos cuando se cambia la moneda, el "enlace dinámico" a través de `CDaoRecordset::GetFieldValue` y `CDaoRecordset::SetFieldValue` puede ser el método de acceso a datos de su elección.

> [!NOTE]
>  DFX y el enlace dinámico no son mutuamente excluyentes, por lo que se puede usar un uso híbrido de enlaces estáticos y dinámicos.

## <a name="_mfcnotes_tn053_examples"></a>Ejemplo 1: uso del intercambio de campos de registros DAO únicamente

(supone `CDaoRecordset`: la clase derivada `CMySet` ya está abierta)

```
// Add a new record to the customers table
myset.AddNew();

myset.m_strCustID = _T("MSFT");

myset.m_strCustName = _T("Microsoft");

myset.Update();
```

**Ejemplo 2: uso de enlace dinámico únicamente**

(se asume que se usa `CDaoRecordset` clase, `rs`y ya está abierto).

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

**Ejemplo 3: uso del intercambio de campos de registros DAO y enlace dinámico**

(se supone que se examinan los datos de empleados con la clase derivada de `CDaoRecordset``emp`)

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

## <a name="_mfcnotes_tn053_how_dfx_works"></a>Cómo funciona DFX

El mecanismo DFX funciona de forma similar al mecanismo de intercambio de campos de registros (RFX) utilizado por las clases ODBC de MFC. Los principios de DFX y RFX son los mismos, pero hay numerosas diferencias internas. El diseño de las funciones DFX era tal que casi todo el código es compartido por las rutinas DFX individuales. En el nivel más alto, DFX solo hace algunas cosas.

- DFX crea la cláusula SQL **Select** y la cláusula SQL **Parameters** si es necesario.

- DFX crea la estructura de enlace utilizada por la función `GetRows` de DAO (más información más adelante).

- DFX administra el búfer de datos que se usa para detectar los campos modificados (si se utiliza el almacenamiento en búfer doble)

- DFX administra las matrices de estado **null** y **Dirty** y establece los valores si es necesario en las actualizaciones.

En el núcleo del mecanismo DFX se encuentra la función `DoFieldExchange` de `CDaoRecordset` clase derivada. Esta función envía llamadas a las funciones DFX individuales de un tipo de operación adecuado. Antes de llamar a `DoFieldExchange` las funciones internas de MFC establecen el tipo de operación. En la lista siguiente se muestran los distintos tipos de operación y una breve descripción.

|Operación|Descripción|
|---------------|-----------------|
|`AddToParameterList`|Compilar parámetros (cláusula)|
|`AddToSelectList`|Cláusulas SELECT de compilaciones|
|`BindField`|Configura la estructura de enlace|
|`BindParam`|Establece los valores de parámetro|
|`Fixup`|Establece el estado NULL|
|`AllocCache`|Asigna caché para comprobación de errores|
|`StoreField`|Guarda el registro actual en la memoria caché|
|`LoadField`|Restaura la memoria caché a los valores de miembro|
|`FreeCache`|Libera memoria caché|
|`SetFieldNull`|Establece el estado de campo & valor en NULL|
|`MarkForAddNew`|Marca los campos como modificados si no es un PSEUDO nulo|
|`MarkForEdit`|Marca los campos como modificados si no coinciden con caché|
|`SetDirtyField`|Establece valores de campo marcados como modificados|

En la siguiente sección, cada operación se explicará con más detalle para `DFX_Text`.

La característica más importante para comprender el proceso de intercambio de campos de registros DAO es que utiliza la función `GetRows` del objeto `CDaoRecordset`. La función `GetRows` de DAO puede funcionar de varias maneras. En esta nota técnica solo se describen brevemente `GetRows`, ya que está fuera del ámbito de esta nota técnica.
Los `GetRows` DAO pueden funcionar de varias maneras.

- Puede capturar varios registros y varios campos de datos al mismo tiempo. Esto permite un acceso más rápido a los datos con la complicación de tratar con una estructura de datos de gran tamaño y con los desplazamientos adecuados para cada campo y para cada registro de datos de la estructura. MFC no aprovecha este mecanismo de obtención de registros múltiples.

- Otra forma de trabajar `GetRows` es permitir que los programadores especifiquen direcciones de enlace para los datos recuperados de cada campo de un registro de datos.

- DAO también devolverá la llamada al llamador para las columnas de longitud variable con el fin de permitir que el llamador asigne memoria. Esta segunda característica tiene la ventaja de minimizar el número de copias de datos, así como permitir el almacenamiento directo de datos en miembros de una clase (la clase derivada `CDaoRecordset`). Este segundo mecanismo es el método que utiliza MFC para enlazar a miembros de datos en `CDaoRecordset` clases derivadas.

##  <a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a>Lo que hace la rutina DFX personalizada

Es evidente que en esta explicación la operación más importante implementada en cualquier función DFX debe ser la capacidad de configurar las estructuras de datos necesarias para llamar correctamente a `GetRows`. Hay una serie de operaciones que una función DFX debe admitir también, pero ninguna como importante o compleja como preparación adecuada para la llamada `GetRows`.

El uso de DFX se describe en la documentación en línea. Esencialmente, hay dos requisitos. En primer lugar, se deben agregar miembros a la clase derivada `CDaoRecordset` para cada campo y parámetro enlazado. Se debe invalidar el siguiente `CDaoRecordset::DoFieldExchange`. Tenga en cuenta que el tipo de datos del miembro es importante. Debe coincidir con los datos del campo de la base de datos o, al menos, ser convertible a ese tipo. Por ejemplo, un campo numérico en la base de datos, como un entero largo, siempre se puede convertir en texto y enlazarse a un miembro de `CString`, pero es posible que un campo de texto de una base de datos no se convierta necesariamente en una representación numérica, como un entero largo y enlazado a un miembro de entero largo. DAO y el motor de base de datos de Microsoft Jet son responsables de la conversión (en lugar de MFC).

##  <a name="_mfcnotes_tn053_details_of_dfx_text"></a>Detalles de DFX_Text

Como se mencionó anteriormente, la mejor manera de explicar cómo funciona DFX es trabajar a través de un ejemplo. Para ello, el uso interno de `DFX_Text` debe funcionar bien para ayudar a proporcionar al menos un conocimiento básico de DFX.

- `AddToParameterList`

   Esta operación genera la cláusula SQL **Parameters** ("`Parameters <param name>, <param type> ... ;`") requerida por jet. Cada parámetro se denomina y se escribe (tal y como se especifica en la llamada RFX). Vea la función `CDaoFieldExchange::AppendParamType` función para ver los nombres de los tipos individuales. En el caso de `DFX_Text`, el tipo utilizado es **Text**.

- `AddToSelectList`

   Compila la cláusula **Select** de SQL. Esto es bastante sencillo, ya que simplemente se anexa el nombre de columna especificado por la llamada DFX ("`SELECT <column name>, ...`").

- `BindField`

   La más compleja de las operaciones. Como se mencionó anteriormente, aquí es donde está configurada la estructura de enlace DAO utilizada por `GetRows`. Como puede ver en el código de `DFX_Text` los tipos de información de la estructura incluyen el tipo de DAO utilizado (**DAO_CHAR** o **DAO_WCHAR** en el caso de `DFX_Text`). Además, también se configura el tipo de enlace utilizado. En una sección anterior `GetRows` se describía solo brevemente, pero era suficiente explicar que el tipo de enlace utilizado por MFC es siempre el enlace de dirección directo (**DAOBINDING_DIRECT**). Además de los enlaces de columna de longitud variable (como `DFX_Text`), se usa el enlace de devolución de llamada para que MFC pueda controlar la asignación de memoria y especificar una dirección de la longitud correcta. Esto significa que MFC siempre puede indicar a DAO "Dónde" colocar los datos, lo que permite el enlace directo a variables de miembro. El resto de la estructura de enlace se rellena con elementos como la dirección de la función de devolución de llamada de asignación de memoria y el tipo de enlace de columna (enlazado por nombre de columna).

- `BindParam`

   Se trata de una operación sencilla que llama a `SetParamValue` con el valor de parámetro especificado en el miembro del parámetro.

- `Fixup`

   Rellena el estado **null** para cada campo.

- `SetFieldNull`

   Esta operación solo marca el estado de cada campo como **null** y establece el valor de la variable miembro en **PSEUDO_NULL**.

- `SetDirtyField`

   Llama a `SetFieldValue` para cada campo marcado como modificado.

Todas las operaciones restantes solo se ocupan del uso de la memoria caché de datos. La memoria caché de datos es un búfer adicional de los datos en el registro actual que se usa para facilitar ciertas cosas. Por ejemplo, los campos "sucios" se pueden detectar automáticamente. Tal y como se describe en la documentación en línea, se puede desactivar por completo o en el nivel de campo. La implementación del búfer emplea una asignación. Esta asignación se usa para hacer coincidir las copias de los datos asignadas dinámicamente con la dirección del campo "enlazado" (o `CDaoRecordset` miembro de datos derivado).

- `AllocCache`

   Asigna dinámicamente el valor del campo almacenado en caché y lo agrega a la asignación.

- `FreeCache`

   Elimina el valor de campo almacenado en memoria caché y lo quita de la asignación.

- `StoreField`

   Copia el valor del campo actual en la memoria caché de datos.

- `LoadField`

   Copia el valor almacenado en caché en el miembro de campo.

- `MarkForAddNew`

   Comprueba si el valor del campo actual no es**null** y lo marca como sucio si es necesario.

- `MarkForEdit`

   Compara el valor actual del campo con la memoria caché de datos y marca los modificados si es necesario.

> [!TIP]
> Modelar las rutinas DFX personalizadas en las rutinas DFX existentes para los tipos de datos estándar.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
