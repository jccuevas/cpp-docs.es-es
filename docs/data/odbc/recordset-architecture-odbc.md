---
title: "Conjunto de registros: Arquitectura (ODBC) | Microsoft Docs"
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
  - "miembros de datos de campo"
  - "miembros de datos de campo, arquitectura de conjuntos de registros"
  - "m_nFields (miembro de datos)"
  - "m_nFields (miembro de datos), conjuntos de registros"
  - "m_nParams (miembro de datos)"
  - "m_nParams (miembro de datos), conjuntos de registros"
  - "conjuntos de registros ODBC, arquitectura"
  - "miembros de datos de parámetros en conjuntos de registros"
  - "conjuntos de registros, arquitectura"
  - "conjuntos de registros, miembros de datos"
ms.assetid: 47555ddb-11be-4b9e-9b9a-f2931764d298
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Conjunto de registros: Arquitectura (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema es aplicable a las clases ODBC de MFC.  
  
 Este tema describe los miembros de datos que componen la arquitectura de un objeto de conjunto de registros:  
  
-   [Miembros de datos de campos](#_core_field_data_members)  
  
-   [Miembros de datos de parámetros](#_core_parameter_data_members)  
  
-   [Utilizar los miembros de datos m\_nFields y m\_nParams](#_core_using_m_nfields_and_m_nparams)  
  
> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas.  Si se implementa la obtención masiva de filas, la arquitectura es similar.  Para comprender mejor estas diferencias, vea [Conjunto de registros: Obtener registros de forma masiva \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_a_sample_class"></a> Clase de ejemplo  
 Al utilizar el [Asistente para consumidores ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) desde el asistente **Agregar clase** para declarar una clase de conjunto de registros derivada de `CRecordset`, la clase resultante tiene la estructura general mostrada en la siguiente clase sencilla:  
  
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
  
 Al comienzo de la clase, el asistente agrega un conjunto de [miembros de datos de campo](#_core_field_data_members).  Cuando se crea la clase, se deben especificar uno o varios miembros de datos de campo.  Si la clase está parametrizada, como lo está la clase de ejemplo \(con el miembro de datos `m_strIDParam`\), se deben agregar manualmente [miembros de datos de parámetro](#_core_parameter_data_members).  El asistente no permite agregar parámetros a una clase.  
  
##  <a name="_core_field_data_members"></a> Miembros de datos de campo  
 Los miembros más importantes de una clase de conjunto de registros son los miembros de datos de campo.  Por cada columna seleccionada en el origen de datos, la clase contiene un miembro de datos del tipo de datos correspondiente a esa columna.  Por ejemplo, la [clase de ejemplo](#_core_a_sample_class) mostrada al comienzo del tema tiene dos miembros de datos de campo, ambos de tipo `CString`, denominados `m_strCourseID` y `m_strCourseTitle`.  
  
 Cuando el conjunto de registros selecciona un conjunto de registros, el marco de trabajo enlaza automáticamente las columnas del registro actual \(después de la llamada a **Open**, el primer registro es actual\) con los miembros de datos de campo del objeto.  Es decir, el marco de trabajo usa el miembro de datos de campo apropiado como búfer en el cual almacena el contenido de una columna de registros.  
  
 A medida que el usuario se desplaza a un nuevo registro, el marco de trabajo usa los miembros de datos de campo para representar el registro actual.  El marco de trabajo actualiza los miembros de datos de campo, reemplazando los valores del registro actual.  Los miembros de datos de campo también se utilizan para actualizar el registro actual y agregar nuevos registros.  Como parte del proceso de actualizar un registro, se especifican los valores de actualización asignando valores directamente al miembro o miembros de datos de campo que corresponda.  
  
##  <a name="_core_parameter_data_members"></a> Miembros de datos de parámetro  
 Si la clase está parametrizada, tiene uno o varios miembros de datos de parámetro.  Una clase parametrizada permite basar una consulta de conjunto de registros en información obtenida o calculada en tiempo de ejecución.  
  
 Normalmente, el parámetro ayuda a restringir la selección, como en el ejemplo siguiente.  Basándose en la [clase de ejemplo](#_core_a_sample_class) del comienzo de este tema, el objeto de conjunto de registros puede ejecutar la siguiente instrucción SQL:  
  
```  
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = ?  
```  
  
 El signo "?" es un marcador de posición para un valor de parámetro que se especifica en tiempo de ejecución.  Al crear el conjunto de registros y establecer el miembro de datos `m_strIDParam` en MATH101, la instrucción SQL efectiva para el conjunto de registros se convierte en:  
  
```  
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = MATH101  
```  
  
 Al definir los miembros de datos de parámetro, se informa al marco de trabajo acerca de los parámetros de la cadena SQL.  El marco de trabajo enlaza el parámetro que permite a ODBC saber dónde obtener valores para usar en sustitución del marcador de posición.  En el ejemplo, el conjunto de registros resultante contiene sólo el registro de la tabla Course con una columna CourseID cuyo valor es MATH101.  Todas las columnas especificadas de este registro están seleccionadas.  Se pueden especificar tantos parámetros \(y marcadores de posición\) como sea necesario.  
  
> [!NOTE]
>  La biblioteca MFC no hace nada por sí misma con los parámetros; en concreto, no realiza ninguna sustitución de texto.  En su lugar, MFC indica a ODBC dónde obtener el parámetro; ODBC recupera los datos y realiza la parametrización necesaria.  
  
> [!NOTE]
>  El orden de los parámetros es importante.  Para obtener información acerca de ésta y otra información sobre parámetros, vea [Conjunto de registros: Parametrizar un conjunto de registros \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
##  <a name="_core_using_m_nfields_and_m_nparams"></a> Utilizar m\_nFields y m\_nParams  
 Cuando un asistente agrega un constructor para la clase, también inicializa el miembro de datos [m\_nFields](../Topic/CRecordset::m_nFields.md) que especifica el número de [miembros de datos de campo](#_core_field_data_members) de la clase.  Si agrega [parámetros](#_core_parameter_data_members) a la clase, también debe agregar un código de inicialización para el miembro de datos [m\_nParams](../Topic/CRecordset::m_nParams.md) que especifica el número de miembros de datos de parámetro.  El marco de trabajo utiliza estos valores para trabajar con los miembros de datos.  
  
 Para obtener más información y ejemplos, vea [Intercambio de campos de registros: Utilizar RFX](../../data/odbc/record-field-exchange-using-rfx.md).  
  
## Vea también  
 [Conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Declarar una clase para una tabla \(ODBC\)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [Intercambio de campos de registros \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)