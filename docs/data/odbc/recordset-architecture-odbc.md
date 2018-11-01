---
title: 'Conjunto de registros: Arquitectura (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, data members
- field data members, recordset architecture
- field data members
- m_nParams data member, recordsets
- recordsets, architecture
- parameter data members in recordsets
- m_nFields data member
- ODBC recordsets, architecture
- m_nParams data member
- m_nFields data member, recordsets
ms.assetid: 47555ddb-11be-4b9e-9b9a-f2931764d298
ms.openlocfilehash: fc44f2b4fcae51cef78d6b660f0cc86ee516e5e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651196"
---
# <a name="recordset-architecture-odbc"></a>Conjunto de registros: Arquitectura (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

En este tema se describe a los miembros de datos que componen la arquitectura de un objeto de conjunto de registros:

- [Miembros de datos](#_core_field_data_members)

- [Miembros de datos de parámetro](#_core_parameter_data_members)

- [Uso de los miembros de datos m_nFields y m_nParams](#_core_using_m_nfields_and_m_nparams)

> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si se implementa la obtención masiva de filas, la arquitectura es similar. Para comprender las diferencias, consulte [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="_core_a_sample_class"></a> Clase de ejemplo

Cuando se usa el [Asistente para consumidores ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) desde **Agregar clase** deriva el Asistente para declarar una clase de conjunto de registros `CRecordset`, la clase resultante tiene la estructura general que se muestra en la siguiente simple clase:

```cpp
class CCourse : public CRecordset
{
public:
   CCourse(CDatabase* pDatabase = NULL);
   ...
   CString m_strCourseID;
   CString m_strCourseTitle;
   CString m_strIDParam;
};
```

Al principio de la clase, el asistente escribe un conjunto de [miembros de datos de campo](#_core_field_data_members). Cuando se crea la clase, debe especificar a uno o varios miembros de datos de campo. Si la clase está parametrizada, como en el ejemplo de clase es (con el miembro de datos `m_strIDParam`), debe agregar manualmente [los miembros de datos de parámetro](#_core_parameter_data_members). El asistente no admite la adición de parámetros a una clase.

##  <a name="_core_field_data_members"></a> Miembros de datos

Los miembros de la clase de conjunto de registros más importantes son los miembros de datos de campo. Para cada columna seleccionada del origen de datos, la clase contiene a un miembro de datos del tipo de datos adecuado para esa columna. Por ejemplo, el [ejemplo clase](#_core_a_sample_class) mostrada al principio de este tema tiene dos miembros de datos de campo, ambos de tipo `CString`, llamado `m_strCourseID` y `m_strCourseTitle`.

Cuando el conjunto de registros, selecciona un conjunto de registros, el marco de trabajo enlaza automáticamente las columnas del registro actual (después de que el `Open` llamada, el primer registro es actual) a los miembros de datos de campo del objeto. Es decir, el marco de trabajo usa al miembro de datos de campo apropiado como búfer en el que se va a almacenar el contenido de una columna de registro.

Cuando el usuario se desplaza a un nuevo registro, el marco de trabajo usa a los miembros de datos de campo para representar el registro actual. El marco de trabajo actualiza a los miembros de datos de campo, reemplazando los valores del registro anterior. Los miembros de datos de campo también se usan para actualizar el registro actual y agregar nuevos registros. Como parte del proceso de actualizar un registro, se especifican los valores de actualización asignando valores directamente al miembro de datos de campo apropiado o miembros.

##  <a name="_core_parameter_data_members"></a> Miembros de datos de parámetro

Si la clase está parametrizada, tiene uno o más miembros de datos de parámetro. Una clase parametrizada permite basar una consulta de conjunto de registros en la información obtenida o calculada en tiempo de ejecución.

Normalmente, el parámetro ayuda a restringir la selección, como en el ejemplo siguiente. Según el [ejemplo clase](#_core_a_sample_class) al principio de este tema, el objeto de conjunto de registros puede ejecutar la instrucción SQL siguiente:

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = ?
```

El "?" es un marcador de posición para un valor de parámetro que se proporciona en tiempo de ejecución. Al construir el conjunto de registros y establezca su `m_strIDParam` MATH101 miembro de datos, se convierte en la instrucción SQL efectiva para el conjunto de registros:

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = MATH101
```

Al definir los miembros de datos de parámetro, indicar al marco acerca de los parámetros de la cadena SQL. El marco de trabajo enlaza el parámetro, que permite a ODBC saber dónde obtener valores para sustituir el marcador de posición. En el ejemplo, el conjunto de registros resultante contiene solo el registro de la tabla Course con una columna CourseID cuyo valor es MATH101. Se seleccionan todas las columnas especificadas de este registro. Puede especificar tantos parámetros (y marcadores de posición) según sea necesario.

> [!NOTE]
>  MFC no hace nada por sí misma con los parámetros, en concreto, no realiza una sustitución de texto. En su lugar, MFC indica ODBC dónde obtener el parámetro; ODBC recupera los datos y realiza la parametrización necesaria.

> [!NOTE]
>  Es importante el orden de parámetros. Para obtener información sobre este y obtener más información acerca de los parámetros, vea [conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

##  <a name="_core_using_m_nfields_and_m_nparams"></a> Utilizar m_nFields y m_nParams

Cuando un asistente, escribe un constructor para la clase, también inicializa la [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) miembro de datos, que especifica el número de [miembros de datos de campo](#_core_field_data_members) en la clase. Si agrega [parámetros](#_core_parameter_data_members) a la clase, también debe agregar código de inicialización para la [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) miembro de datos, que especifica el número de miembros de datos de parámetro. El marco de trabajo usa estos valores para trabajar con los miembros de datos.

Para obtener más información y ejemplos, vea [intercambio de campos de registros: Utilizar RFX](../../data/odbc/record-field-exchange-using-rfx.md).

## <a name="see-also"></a>Vea también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Declarar una clase para una tabla (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)