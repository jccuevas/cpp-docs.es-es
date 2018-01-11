---
title: 'TN043: Rutinas RFX | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: RFX
dev_langs: C++
helpviewer_keywords:
- RFX (record field exchange), architecture
- TN043
- RFX (record field exchange)
ms.assetid: f552d0c1-2c83-4389-b472-42c9940aa713
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 19bb44653c03505d954318a01a6e34c1a297dba7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="tn043-rfx-routines"></a>TN043: Rutinas RFX
> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota describe la arquitectura de campos de registros (RFX) de exchange. También se describe cómo escribir un **RFX_** procedimiento.  
  
## <a name="overview-of-record-field-exchange"></a>Información general de intercambio de campos de registro  
 Todas las funciones de campo de conjunto de registros se realizan con el código de C++. No hay recursos especiales ni mágicas macros. El núcleo del mecanismo de es una función virtual que se debe invalidar en cada clase derivada de conjunto de registros. Siempre se encuentra en este formato:  
  
```  
void CMySet::DoFieldExchange(CFieldExchange* pFX)  
{ *//{{AFX_FIELD_MAP(CMySet)  
 <recordset exchange field type call>  
 <recordset exchange function call> *//}}AFX_FIELD_MAP  
}  
```  
  
 Los comentarios de formato especiales AFX permiten ClassWizard localizar y editar el código dentro de esta función. Código que no es compatible con ClassWizard debe colocarse fuera de los comentarios de formato especiales.  
  
 En el ejemplo anterior, < recordset_exchange_field_type_call > tiene el formato:  
  
```  
pFX->SetFieldType(CFieldExchange::outputColumn);
```  
  
 y < recordset_exchange_function_call > tiene el formato:  
  
```  
RFX_Custom(pFX, "Col2",
    m_Col2);
```  
  
 La mayoría **RFX_** funciones tienen tres argumentos, como se indicó anteriormente, pero algunos (p. ej. `RFX_Text` y `RFX_Binary`) tienen argumentos opcionales adicionales.  
  
 Más de un **RFX_** en cada uno de ellos pueden incluirse `DoDataExchange` función.  
  
 Vea 'afxdb.h' para obtener una lista de todas las rutinas de intercambio de campos de conjunto de registros que se proporcionadas por MFC.  
  
 Llamadas de campo de conjunto de registros son una manera de registrar ubicaciones de memoria (normalmente los miembros de datos) para almacenar datos de campo de un **CMySet** clase.  
  
## <a name="notes"></a>Notas  
 Funciones de campo de conjunto de registros están diseñadas para funcionar solo con el `CRecordset` clases. No son por lo general puede usar cualquier otra clase MFC.  
  
 Los valores iniciales de los datos se establecen en el constructor de C++ estándar, por lo general en un bloque con `//{{AFX_FIELD_INIT(CMylSet)` y `//}}AFX_FIELD_INIT` comentarios.  
  
 Cada **RFX_** función debe admitir varias operaciones, comprendido entre devolver el estado del campo modificado para archivar el campo como preparación para editar el campo.  
  
 Cada función que llama a `DoFieldExchange` (por ejemplo `SetFieldNull`, `IsFieldDirty`), realiza su propia inicialización alrededor de la llamada a `DoFieldExchange`.  
  
## <a name="how-does-it-work"></a>¿Cómo funciona  
 No es necesario entender lo siguiente para utilizar el intercambio de campos de registros. Sin embargo, entender cómo funciona en segundo plano le ayudarán a escribir su propio procedimiento de exchange.  
  
 El `DoFieldExchange` función miembro es muy similar a la `Serialize` función miembro, es responsable de obtener o establecer datos de forma externa (en este caso columnas del resultado de una consulta ODBC) y los datos de miembro de la clase. El `pFX` parámetro es el contexto para realizar el intercambio de datos y es similar a la `CArchive` parámetro `CObject::Serialize`. El `pFX` (un `CFieldExchange` objeto) tiene un indicador de operación, que es similar a, pero una generalización de las `CArchive` marca de dirección. Puede tener una función RFX para admitir las operaciones siguientes:  
  
- **BindParam** : indique dónde ODBC debe recuperar los datos del parámetro  
  
- **BindFieldToColumn** : indique dónde ODBC debe recuperar/depósito outputColumn datos  
  
- **Corrección** : establecer **CString/CByteArray** longitudes, establecer el estado NULL de bits  
  
- **MarkForAddNew** : marca desfasadas si el valor ha cambiado desde que se llame AddNew  
  
- **MarkForUpdate** : marca desfasadas si el valor ha cambiado desde que se llame editar  
  
- **Nombre** : anexar nombres de campo para los campos marcados como modificados  
  
- **NameValue** : anexar "\<nombre de columna > =" para los campos marcados como modificados  
  
- **Valor** : anexar "" seguido de separador, al igual que ',' o ' '  
  
- `SetFieldDirty`: Establezca el campo de estado bits desfasadas (es decir, cambiado)  
  
- `SetFieldNull`: Establezca el bit de estado que indica el valor null para el campo  
  
- `IsFieldDirty`: Devuelve el valor de bit de integridad de estado  
  
- `IsFieldNull`: Devuelve el valor de bit de estado null  
  
- `IsFieldNullable`: Devuelve TRUE si el campo puede contener valores NULL  
  
- **StoreField** : valor de campo de archivo  
  
- **LoadField** : volver a cargar archiva el valor del campo  
  
- **GetFieldInfoValue** : devolver información general sobre un campo  
  
- **GetFieldInfoOrdinal** : devolver información general sobre un campo  
  
## <a name="user-extensions"></a>Extensiones de usuario  
 Hay varias maneras de extender el mecanismo RFX predeterminado. Puede  
  
-   Agregar nuevos tipos de datos. Por ejemplo:  
  
 ```  
    CBookmark 
 ```  
  
-   Agregar nuevos procedimientos de exchange (RFX_).  
  
 ```  
    void AFXAPI RFX_Bigint(CFieldExchange* pFX,
    const char *szName,  
    BIGINT& value);

 ```  
  
-   Tiene la `DoFieldExchange` función miembro incluyen de forma condicional llamadas RFX adicionales o cualquier otra instrucción de C++ válido.  
  
 ```  
    while (posExtraFields != NULL)  
 {  
    RFX_Text(pFX,
    m_listName.GetNext(posExtraFields),   
    m_listValue.GetNext(posExtraValues));

 }  
 ```  
  
> [!NOTE]
>  Este código no puede ser editado por ClassWizard y debe utilizarse solo fuera de los comentarios de formato especiales.  
  
## <a name="writing-a-custom-rfx"></a>Escribir un RFX personalizado  
 Para escribir su propia función RFX personalizado, se recomienda que copie una función RFX existente y modificarlo para sus propios fines. Al seleccionar el RFX derecho para copiar puede facilitar el trabajo mucho más fácil. Algunas funciones RFX tienen algunas propiedades únicas que debe tener en cuenta al decidir que se va a copiar.  
  
 **RFX_Long y RFX_Int**:  
 Éstas son las funciones RFX más sencillas. El valor de datos no es necesario ninguna interpretación especial y el tamaño de datos es fijo.  
  
 **RFX_Single y RFX_Double**:  
 Al igual que RFX_Long y RFX_Int anteriores, estas funciones son simples y puede hacer mucho el uso de la implementación predeterminada. Se almacenan en dbflt.cpp en lugar de dbrfx.cpp, sin embargo, para habilitar la carga de la biblioteca de punto flotante solo cuando explícitamente se referencia en tiempo de ejecución.  
  
 **RFX_Text y RFX_Binary**:  
 Estas dos funciones preasignar un búfer estático para alojar información de cadena o binarios y deben registrar estos búferes con ODBC SQLBindCol en lugar de registrar y valor. Por este motivo, estas dos funciones tienen una gran cantidad de código de casos especiales.  
  
 `RFX_Date`:  
 ODBC devuelve información de fecha y hora en su propia estructura de datos TIMESTAMP_STRUCT. Esta función asigna dinámicamente un TIMESTAMP_STRUCT como "proxy" para enviar y recibir datos en tiempo de fecha. Varias operaciones deben transferir la información de fecha y hora entre C++ `CTime` objeto y el proxy TIMESTAMP_STRUCT. Esto complica considerablemente esta función, pero es un buen ejemplo de cómo usar a un servidor proxy para la transferencia de datos.  
  
 `RFX_LongBinary`:  
 Se trata de la biblioteca de clases solo función RFX que no usa el enlace de columna para recibir y enviar datos. Esta función pasa por alto la operación BindFieldToColumn y en su lugar, durante la operación de reparación, asigna almacenamiento para almacenar los datos entrantes SQL_LONGVARCHAR o SQL_LONGVARBINARY, a continuación, realiza una llamada de SQLGetData para recuperar el valor en el almacenamiento asignado. Cuando se prepare para devolver valores de datos al origen de datos (por ejemplo, las operaciones de NameValue y valor), esta función sirve DATA_AT_EXEC funcionalidad de ODBC. Vea [Nota técnica 45](../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md) para obtener más información sobre cómo trabajar con SQL_LONGVARBINARY y SQL_LONGVARCHARs.  
  
 Al escribir su propio **RFX_** función, a menudo podrá usar **CFieldExchange::Default** para implementar una operación determinada. Examine la implementación de forma predeterminada para la operación en cuestión. Si realiza la operación tendría que escribir el **RFX_** función puede delegar en el **CFieldExchange::Default.** Puede ver ejemplos de llamar al método **CFieldExchange::Default** en dbrfx.cpp  
  
 Es importante llamar a `IsFieldType` al principio de la función RFX y volver inmediatamente si devuelve FALSE. Este mecanismo mantiene lleve a cabo en operaciones parámetro **outputColumns**y viceversa (como llamar a **BindParam** en un **outputColumn**). Además, `IsFieldType` automáticamente realiza un seguimiento del recuento de **outputColumns** (`m_nFields`) y los parámetros de (`m_nParams`).  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

