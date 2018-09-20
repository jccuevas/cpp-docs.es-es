---
title: 'TN053: Personalizar las rutinas DFX para DAO base de datos clases | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.dfx
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 054ff12e47d2a6bd38d1a51a7745e5b3916c90dc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445118"
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>TN053: Personalizar las rutinas DFX para las clases de base de datos DAO

> [!NOTE]
>  El entorno de Visual C++ y los asistentes no admiten DAO (aunque las clases DAO están incluidas y puede seguir usándolos). Microsoft recomienda que utilice [plantillas OLE DB](../data/oledb/ole-db-templates.md) o [ODBC y MFC](../data/odbc/odbc-and-mfc.md) para los proyectos nuevos. Sólo se debe utilizar DAO mantener las aplicaciones existentes.

Esta nota técnica describe el mecanismo de intercambio (DFX) de campos de registros DAO. Para ayudar a entender lo que sucede en las rutinas DFX, la `DFX_Text` función se explican en detalle como ejemplo. Como una fuente de información para esta nota técnica adicional, puede examinar el código para los demás las funciones DFX individuales. Probablemente no necesitará una rutina DFX personalizada tan a menudo como es posible que necesite una rutina RFX personalizada (que se utiliza con las clases de base de datos ODBC).

Esta nota técnica contiene:

- Información general DFX

- [Ejemplos](#_mfcnotes_tn053_examples) utilizando intercambio de campos de registros DAO y enlace dinámico

- [Cómo funciona DFX](#_mfcnotes_tn053_how_dfx_works)

- [Lo que hace su rutina DFX personalizadas](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)

- [Detalles de DFX_Text](#_mfcnotes_tn053_details_of_dfx_text)

**Información general DFX**

El mecanismo de intercambio de campos de registros DAO (DFX) se usa para simplificar el procedimiento de recuperación y actualización de datos cuando se usa el `CDaoRecordset` clase. El proceso se ha simplificado mediante miembros de datos de la `CDaoRecordset` clase. Al derivar de `CDaoRecordset`, puede agregar miembros de datos a la clase derivada que representa cada campo en una tabla o consulta. Este mecanismo de "enlace estático" es sencillo, pero no puede ser el método de captura o actualización de datos de elección para todas las aplicaciones. DFX recupera cada campo enlazado a cada vez que cambia el registro actual. Si está desarrollando una aplicación sensibles al rendimiento que no requiere que se capturen todos los campos cuando se cambia la divisa, "enlace dinámico" a través de `CDaoRecordset::GetFieldValue` y `CDaoRecordset::SetFieldValue` puede ser el método de acceso a datos de elección.

> [!NOTE]
>  DFX y enlace dinámico no son mutuamente excluyentes, por lo que puede usarse un uso híbrido de enlaces estáticos y dinámicos.

## <a name="_mfcnotes_tn053_examples"></a> Ejemplo 1: Uso de intercambio de campos de registro DAO solo

(se da por supuesto `CDaoRecordset` : clase derivada `CMySet` está abierto)

```
// Add a new record to the customers table
myset.AddNew();

myset.m_strCustID = _T("MSFT");

myset.m_strCustName = _T("Microsoft");

myset.Update();
```

**Ejemplo 2: Uso de solo el enlace dinámico**

(se supone el uso de `CDaoRecordset` (clase), `rs`, y ya está abierto)

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

**Ejemplo 3: Uso del registro de intercambio de campos DAO y enlace dinámico**

(se supone la exploración de datos de empleados con `CDaoRecordset`-clase derivada `emp`)

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

## <a name="_mfcnotes_tn053_how_dfx_works"></a> Cómo funciona DFX

El mecanismo DFX funciona de manera similar al mecanismo campos de registros (RFX) de exchange utilizada por las clases ODBC de MFC. Los principios de RFX y de DFX son los mismos, pero hay numerosas diferencias internas. El diseño de las funciones DFX era que prácticamente todo el código es compartido por las rutinas DFX individuales. En sólo el DFX nivel más alto realiza algunas actividades.

- DFX construcciones SQL **seleccione** cláusula y SQL **parámetros** cláusula si es necesario.

- DFX construye la estructura de enlace utilizada por de DAO `GetRows` función (más información sobre esto más adelante).

- DFX administra el búfer de datos que se usa para detectar los campos modificados (si se usa el búfer doble)

- DFX administra la **NULL** y **DIRTY** estado matrices y establece los valores si es necesario en las actualizaciones.

En el corazón de la DFX mecanismo es el `CDaoRecordset` derivados de la clase `DoFieldExchange` función. Esta función envía llamadas a las funciones DFX individuales de un tipo de operación correspondiente. Antes de llamar a `DoFieldExchange` las funciones MFC internas establecen el tipo de operación. En la lista siguiente se muestra los distintos tipos de operación y una breve descripción.

|Operación|Descripción|
|---------------|-----------------|
|`AddToParameterList`|Cláusula de parámetros de compilaciones|
|`AddToSelectList`|Cláusula SELECT de compilaciones|
|`BindField`|Establece la estructura de enlace|
|`BindParam`|Establece los valores de parámetro|
|`Fixup`|Establece el estado NULL|
|`AllocCache`|Asigna la memoria caché de comprobación de integridad|
|`StoreField`|Guarda el registro actual en memoria caché|
|`LoadField`|Restauraciones de caché para los valores de miembro|
|`FreeCache`|Libera la memoria caché|
|`SetFieldNull`|Conjuntos de campo de valor a NULL & estado|
|`MarkForAddNew`|Marca los campos de datos sucios si no NULL de PSEUDO|
|`MarkForEdit`|If desfasada de los campos de marcas no coinciden con la memoria caché|
|`SetDirtyField`|Campo de conjuntos de valores que se marcan con errores|

En la sección siguiente, cada operación se explicará con más detalle para `DFX_Text`.

La característica más importante para entender sobre el proceso de intercambio de campos de registros DAO es que usa el `GetRows` función de la `CDaoRecordset` objeto. DAO `GetRows` la función puede funcionar de varias maneras. Esta nota técnica describirá brevemente `GetRows` aunque sea fuera del ámbito de esta nota técnica.

DAO `GetRows` puede trabajar de varias maneras.

- Pueden capturar registros de varios y varios campos de datos al mismo tiempo. Esto permite obtener acceso a datos más rápido con la complicación de tratar con una estructura de datos de gran tamaño y los desplazamientos correspondientes a cada campo y para cada registro de datos de la estructura. MFC no aprovechar las ventajas de este registro varios mecanismo de captura.

- Otra manera de `GetRows` puede trabajo consiste en permitir a los programadores especificar direcciones de enlace para los datos recuperados de cada campo de un registro de datos.

- DAO le también "volver a llamar" en el llamador para columnas de longitud variable con el fin de permitir que el llamador asignar memoria. Esta segunda característica tiene la ventaja de reducir el número de copias de datos, así como permitir almacenamiento directo de datos en los miembros de una clase (la `CDaoRecordset` clase derivada). Este segundo mecanismo es el método MFC utiliza para enlazar a los miembros de datos en `CDaoRecordset` las clases derivadas.

##  <a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a> Lo que hace su rutina DFX personalizadas

Es evidente de este análisis, que la operación más importante que se implementa en cualquier función DFX debe ser la capacidad de configurar las estructuras de datos necesarios para llamar correctamente a `GetRows`. Hay una serie de otras operaciones que una función DFX debe admitir también, pero ninguna es tan importante o compleja como preparar correctamente para el `GetRows` llamar.

El uso de DFX se describe en la documentación en línea. Básicamente, hay dos requisitos. En primer lugar, se deben agregar miembros a la `CDaoRecordset` clase derivada para cada parámetro y el campo enlazado. Siga este `CDaoRecordset::DoFieldExchange` debe reemplazarse. Tenga en cuenta que el tipo de datos del miembro es importante. Debe coincidir con los datos del campo de la base de datos o al menos ser convertible a ese tipo. Por ejemplo, un campo numérico en la base de datos, como un entero largo, siempre se convierte en texto y enlazado a un `CString` miembro, pero un campo de texto en una base de datos no necesariamente se puede convertir en una representación numérica, como entero largo y enlazado a un largo integ ER miembro. DAO y el motor de base de datos Microsoft Jet son responsables de la conversión (en lugar de MFC).

##  <a name="_mfcnotes_tn053_details_of_dfx_text"></a> Detalles de DFX_Text

Como se mencionó anteriormente, la mejor manera de explicar cómo funciona DFX es un ejemplo. Para este fin de repasar los aspectos internos de `DFX_Text` debería funcionar bastante bien para ayudar a proporcionar al menos un conocimiento básico de DFX.

- `AddToParameterList`

   Esta operación basa el SQL **parámetros** cláusula ("`Parameters <param name>, <param type> ... ;`") requiere Jet. Cada parámetro es llamado y escribe (según lo especificado en la llamada RFX). Vea la función `CDaoFieldExchange::AppendParamType` función para ver los nombres de los tipos individuales. En el caso de `DFX_Text`, el tipo utilizado es **texto**.

- `AddToSelectList`

   Compila el código SQL **seleccione** cláusula. Esto es bastante sencillo como el nombre de columna especificado por la llamada DFX es simplemente anexan ("`SELECT <column name>, ...`").

- `BindField`

   La más compleja de las operaciones. Como se mencionó anteriormente es donde usa la estructura de enlace de DAO `GetRows` se ha configurado. Como puede ver en el código de `DFX_Text` los tipos de información de la estructura de incluyen el tipo DAO utilizado (**DAO_CHAR** o **DAO_WCHAR** en el caso de `DFX_Text`). Además, también se establece el tipo de enlace que se usa. En una sección anterior `GetRows` se describen brevemente, pero era suficiente explicar que el tipo de enlace usada por MFC siempre es el enlace de dirección directa (**DAOBINDING_DIRECT**). Además, para el enlace de columna de longitud variable (como `DFX_Text`) se utiliza el enlace de devolución de llamada para que pueda controlar la asignación de memoria y especificar una dirección de la longitud correcta de MFC. Esto significa que MFC siempre puede deducir a DAO "where" colocar los datos, lo que permite el enlace directamente a las variables miembro. El resto de la estructura de enlace se rellena con cosas como la dirección de la función de devolución de llamada de asignación de memoria y el tipo de enlace de columna (enlace por nombre de columna).

- `BindParam`

   Se trata de una operación sencilla que llama a `SetParamValue` con el valor del parámetro especificado en el miembro de parámetro.

- `Fixup`

   Rellena el **NULL** estado para cada campo.

- `SetFieldNull`

   Esta operación solo marca cada estado del campo como **NULL** y establece el miembro de la variable en **PSEUDO_NULL**.

- `SetDirtyField`

   Las llamadas `SetFieldValue` para cada campo marcado como modificado.

Todas las operaciones restantes solo se tratan con el uso de la caché de datos. La caché de datos es un búfer adicional de los datos en el registro actual que se usa para simplificar ciertas cosas. Por ejemplo, pueden detectar automáticamente los campos "sucios". Como se describe en la documentación en línea que se puede desactivar completamente o en el nivel de campo. La implementación del búfer utiliza un mapa. Esta asignación se utiliza para hacer coincidir asignadas dinámicamente copias de los datos con la dirección del campo "enlazado" (o `CDaoRecordset` derivados de miembro de datos).

- `AllocCache`

   Asigna el valor del campo en caché y lo agrega a la asignación dinámicamente.

- `FreeCache`

   Elimina el valor del campo en caché y lo quita de la asignación.

- `StoreField`

   Copia el valor del campo actual en la caché de datos.

- `LoadField`

   Copia el valor almacenado en caché en el miembro de campo.

- `MarkForAddNew`

   Comprueba si el valor del campo actual es que no sean de**NULL** y lo marca como desfasada si es necesario.

- `MarkForEdit`

   Compara el valor actual del campo con la memoria caché de datos y marca de modificado si es necesario.

> [!TIP]
> Modelar sus rutinas DFX personalizadas en las rutinas DFX existentes para los tipos de datos estándar.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

