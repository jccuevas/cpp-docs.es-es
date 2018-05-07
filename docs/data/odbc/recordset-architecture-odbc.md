---
title: 'Conjunto de registros: Arquitectura (ODBC) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5be3ec16ec01a6c6db2e24b1b6a6260f3a44bfec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="recordset-architecture-odbc"></a>Conjunto de registros: Arquitectura (ODBC)
Este tema es aplicable a las clases ODBC de MFC.  
  
 En este tema se describe a los miembros de datos que componen la arquitectura de un objeto de conjunto de registros:  
  
-   [Miembros de datos de campo](#_core_field_data_members)  
  
-   [Miembros de datos de parámetro](#_core_parameter_data_members)  
  
-   [Usar a miembros de datos m_nFields y m_nParams](#_core_using_m_nfields_and_m_nparams)  
  
> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si se implementa la obtención masiva de filas, la arquitectura es similar. Para entender las diferencias, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_a_sample_class"></a> Clase de ejemplo  
 Cuando se usa el [Asistente para consumidores ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) de **Agregar clase** Asistente para declarar una clase de conjunto de registros se deriva de `CRecordset`, la clase resultante tiene la estructura general que se muestra en la siguiente simple clase:  
  
```  
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
  
 Al principio de la clase, el asistente escribe un conjunto de [miembros de datos de campo](#_core_field_data_members). Cuando se crea la clase, debe especificar a uno o varios miembros de datos de campo. Si la clase está parametrizada, como en el ejemplo de clase es (con el miembro de datos `m_strIDParam`), debe agregar manualmente [miembros de datos de parámetro](#_core_parameter_data_members). El asistente no admite la adición de parámetros a una clase.  
  
##  <a name="_core_field_data_members"></a> Miembros de datos de campo  
 Los miembros más importantes de la clase de conjunto de registros son los miembros de datos de campo. Para cada columna que seleccione del origen de datos, la clase contiene a un miembro de datos de tipo de datos adecuado para esa columna. Por ejemplo, el [ejemplo clase](#_core_a_sample_class) mostrada al principio de este tema tiene dos miembros de datos de campo, ambos de tipo `CString`, llamado `m_strCourseID` y `m_strCourseTitle`.  
  
 Cuando el conjunto de registros selecciona un conjunto de registros, el marco de trabajo enlaza automáticamente las columnas del registro actual (después de la **abiertos** llamada, el primer registro es actual) a los miembros de datos de campo del objeto. Es decir, el marco de trabajo usa al miembro de datos de campo apropiado como búfer en el que se va a almacenar el contenido de una columna de registro.  
  
 Cuando el usuario se desplaza a un nuevo registro, el marco de trabajo usa a los miembros de datos de campo para representar el registro actual. El marco de trabajo actualiza a los miembros de datos de campo, reemplazando los valores del registro anterior. Los miembros de datos de campo también se utilizan para actualizar el registro actual y agregar nuevos registros. Como parte del proceso de actualizar un registro, se especifican los valores de actualización asignando valores directamente en el miembro de datos de campo correspondiente o miembros.  
  
##  <a name="_core_parameter_data_members"></a> Miembros de datos de parámetro  
 Si la clase está parametrizada, tiene uno o más miembros de datos de parámetro. Una clase parametrizada permite basar una consulta de conjunto de registros en información obtenida o calculada en tiempo de ejecución.  
  
 Normalmente, el parámetro ayuda a restringir la selección, como en el ejemplo siguiente. En función de la [ejemplo clase](#_core_a_sample_class) al principio de este tema, el objeto de conjunto de registros puede ejecutar la siguiente instrucción SQL:  
  
```  
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = ?  
```  
  
 El "?" es un marcador de posición para un valor de parámetro que se proporciona en tiempo de ejecución. Cuando se construye el conjunto de registros y establezca su `m_strIDParam` miembro de datos en MATH101, se convertirá en la instrucción SQL efectiva para el conjunto de registros:  
  
```  
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = MATH101  
```  
  
 Al definir los miembros de datos de parámetro, el marco de trabajo, saber acerca de los parámetros en la cadena de SQL. El marco de trabajo enlaza el parámetro, que permite a ODBC saber dónde obtener valores para sustituir el marcador de posición. En el ejemplo, el conjunto de registros resultante contiene solo el registro de la tabla Course con una columna CourseID cuyo valor es MATH101. Se seleccionan todas las columnas especificadas de este registro. Puede especificar tantos parámetros (y marcadores de posición) según sea necesario.  
  
> [!NOTE]
>  MFC no hace nada por sí misma con los parámetros, en concreto, no realiza una sustitución de texto. En su lugar, MFC indica a ODBC dónde obtener el parámetro; ODBC recupera los datos y realiza la parametrización necesaria.  
  
> [!NOTE]
>  El orden de parámetros es importante. Para obtener información sobre este y obtener más información acerca de los parámetros, vea [conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
##  <a name="_core_using_m_nfields_and_m_nparams"></a> Utilizar m_nFields y m_nParams  

 Cuando un asistente, escribe un constructor para la clase, también inicializa el [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) miembro de datos, que especifica el número de [miembros de datos de campo](#_core_field_data_members) en la clase. Si agrega cualquier [parámetros](#_core_parameter_data_members) a la clase, debe agregar también una inicialización para el [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) miembro de datos, que especifica el número de miembros de datos de parámetro. El marco de trabajo usa estos valores para trabajar con los miembros de datos.  
  
 Para obtener más información y ejemplos, vea [intercambio de campos de registros: Utilizar RFX](../../data/odbc/record-field-exchange-using-rfx.md).  
  
## <a name="see-also"></a>Vea también  
 [Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Declarar una clase para una tabla (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)