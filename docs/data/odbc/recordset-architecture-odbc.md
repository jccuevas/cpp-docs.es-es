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
ms.openlocfilehash: e95250b5ef307eafdb334050fbace945355e0521
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079861"
---
# <a name="recordset-architecture-odbc"></a>Conjunto de registros: Arquitectura (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

En este tema se describen los miembros de datos que componen la arquitectura de un objeto de conjunto de registros:

- [Miembros de datos de campo](#_core_field_data_members)

- [Miembros de datos de parámetros](#_core_parameter_data_members)

- [Uso de miembros de datos m_nFields y m_nParams](#_core_using_m_nfields_and_m_nparams)

> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si se implementa la obtención masiva de filas, la arquitectura es muy similar. Para comprender las diferencias, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="sample-class"></a><a name="_core_a_sample_class"></a> Clase de ejemplo

> [!NOTE]
> El Asistente para consumidores ODBC de MFC no está disponible en Visual Studio 2019 ni en versiones posteriores. Aun así, puede crear un consumidor de forma manual.

Cuando se usa el [Asistente para consumidores ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) desde el Asistente para **agregar clases** a fin de declarar una clase de conjunto de registros derivada `CRecordset`, la clase resultante tiene la estructura general que se muestra en la siguiente clase de ejemplo:

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

Al principio de la clase, el asistente escribe un conjunto de [miembros de datos de campo](#_core_field_data_members). Al crear la clase, debe especificar uno o varios miembros de datos de campo. Si la clase está parametrizada, como la clase de ejemplo (con el miembro de datos `m_strIDParam`), debe agregar manualmente [miembros de datos de parámetros](#_core_parameter_data_members). El asistente no admite la adición de parámetros a una clase.

##  <a name="field-data-members"></a><a name="_core_field_data_members"></a> Miembros de datos de campo

Los miembros más importantes de la clase de conjunto de registros son los miembros de datos de campo. Para cada columna que haya seleccionado en el origen de datos, la clase contiene un miembro de datos del tipo de datos adecuado para esa columna. Por ejemplo, la [clase de ejemplo](#_core_a_sample_class) mostrada al principio de este tema tiene dos miembros de datos de campo, ambos de tipo `CString`, denominados `m_strCourseID` y `m_strCourseTitle`.

Cuando el conjunto de registros selecciona una serie de registros, el marco enlaza automáticamente las columnas del registro actual (que es el primer registro después de la llamada a `Open`) a los miembros de datos de campo del objeto. Es decir, el marco usa el miembro de datos de campo apropiado como búfer en el que se va a almacenar el contenido de una columna de registro.

Cuando el usuario se desplaza a un nuevo registro, el marco usa los miembros de datos de campo para representar el registro actual. El marco actualiza los miembros de datos de campo y reemplaza los valores del registro anterior. Los miembros de datos de campo también se usan para actualizar el registro actual y agregar nuevos registros. Como parte del proceso para actualizar un registro, debe especificar los valores de actualización. Para ello, asigne los valores directamente a los miembros de datos de campo adecuados.

##  <a name="parameter-data-members"></a><a name="_core_parameter_data_members"></a> Miembros de datos de parámetros

Si la clase está parametrizada, tiene uno o varios miembros de datos de parámetros. Una clase parametrizada permite basar una consulta del conjunto de registros en la información que se ha obtenido o calculado en tiempo de ejecución.

Normalmente, el parámetro ayuda a restringir la selección, como en el ejemplo siguiente. En función de la [clase de ejemplo](#_core_a_sample_class) indicada al principio de este tema, el objeto de conjunto de registros puede ejecutar la siguiente instrucción SQL:

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = ?
```

El símbolo "?" es un marcador de posición para un valor de parámetro que se proporciona en tiempo de ejecución. Cuando construya el conjunto de registros y establezca su miembro de datos `m_strIDParam` en MATH101, la instrucción SQL efectiva para el conjunto de registros se convertirá en lo siguiente:

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = MATH101
```

Al definir miembros de datos de parámetros, le está indicando al marco los parámetros que contiene la cadena SQL. El marco enlaza el parámetro, lo que permite que ODBC sepa dónde debe obtener los valores para sustituir el marcador de posición. En el ejemplo, el conjunto de registros resultante solo contiene el registro de la tabla Course con una columna CourseID, cuyo valor es MATH101. Todas las columnas especificadas de este registro están seleccionadas. Puede especificar tantos parámetros (y marcadores de posición) como necesite.

> [!NOTE]
>  MFC no hace nada específico con los parámetros (en concreto, no realiza una sustitución de texto), pero le indica a ODBC dónde obtener el parámetro, de modo que ODBC pueda recuperar los datos y realizar la parametrización necesaria.

> [!NOTE]
>  El orden de los parámetros es importante. Para obtener información sobre este y más información sobre los parámetros, vea [conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

##  <a name="using-m_nfields-and-m_nparams"></a><a name="_core_using_m_nfields_and_m_nparams"></a> Uso de m_nFields y m_nParams

Cuando un asistente escribe un constructor para la clase, también inicializa el miembro de datos [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields), que especifica el número de [miembros de datos de campo](#_core_field_data_members) de la clase. Si agrega algún [parámetro](#_core_parameter_data_members) a la clase, debe agregar también una inicialización para el miembro de datos [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams), que especifica el número de miembros de datos de parámetros. El marco usa estos valores para trabajar con los miembros de datos.

Para obtener más información y ejemplos, vea [intercambio de campos de registros: utilizar RFX](../../data/odbc/record-field-exchange-using-rfx.md).

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Declarar una clase para una tabla (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)