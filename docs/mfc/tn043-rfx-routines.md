---
title: 'TN043: Rutinas RFX'
ms.date: 06/28/2018
f1_keywords:
- RFX
helpviewer_keywords:
- RFX (record field exchange), architecture
- TN043
- RFX (record field exchange)
ms.assetid: f552d0c1-2c83-4389-b472-42c9940aa713
ms.openlocfilehash: 18820c7d17ddea355490ee32679d5d690ec3533e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305403"
---
# <a name="tn043-rfx-routines"></a>TN043: Rutinas RFX

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota describe la arquitectura de campos de registros (RFX). También se describe cómo escribir un **RFX_** procedimiento.

## <a name="overview-of-record-field-exchange"></a>Información general de intercambio de campos de registro

Todas las funciones de campo de conjunto de registros se realizan con el código de C++. No existen recursos especiales ni macros mágicas. El corazón del mecanismo de es una función virtual que se debe invalidar en todas las clases derivadas del conjunto de registros. Siempre se encuentra en este formulario:

```cpp
void CMySet::DoFieldExchange(CFieldExchange* pFX)
{
    //{{AFX_FIELD_MAP(CMySet)
        <recordset exchange field type call>
        <recordset exchange function call>
    //}}AFX_FIELD_MAP
}
```

Los comentarios de formato especial AFX permiten ClassWizard localizar y editar el código de esta función. Código que no es compatible con ClassWizard debe colocarse fuera de los comentarios de formato especiales.

En el ejemplo anterior, \<recordset_exchange_field_type_call > está en el formulario:

```cpp
pFX->SetFieldType(CFieldExchange::outputColumn);
```

y \<recordset_exchange_function_call > está en el formulario:

```cpp
RFX_Custom(pFX, "Col2", m_Col2);
```

La mayoría **RFX_** funciones tienen tres argumentos, como se indicó anteriormente, pero algunos (por ejemplo, `RFX_Text` y `RFX_Binary`) tienen argumentos opcionales adicionales.

Más de un **RFX_** puede incluirse en cada `DoDataExchange` función.

Consulte 'afxdb.h' para obtener una lista de todas las rutinas de intercambio de campo de conjunto de registros que se proporcionadas por MFC.

Las llamadas de campo de conjunto de registros son una manera de registrar las ubicaciones de memoria (normalmente, los miembros de datos) para almacenar datos de campo para un `CMySet` clase.

## <a name="notes"></a>Notas

Funciones de campo de conjunto de registros están diseñadas para funcionar solo con el `CRecordset` clases. No son generalmente utilizables por otras clases de MFC.

Los valores iniciales de los datos se establecen en el constructor de C++ estándar, por lo general en un bloque con `//{{AFX_FIELD_INIT(CMylSet)` y `//}}AFX_FIELD_INIT` comentarios.

Cada **RFX_** función debe admitir varias operaciones, que abarcan desde devolviendo el estado modificado del campo para archivar el campo como preparación para editar el campo.

Cada función que llama a `DoFieldExchange` (por ejemplo `SetFieldNull`, `IsFieldDirty`), realiza su propia inicialización alrededor de la llamada a `DoFieldExchange`.

## <a name="how-does-it-work"></a>¿Cómo funciona

No es necesario entender los siguientes conceptos para poder usar el intercambio de campos de registros. Sin embargo, comprender cómo funciona en segundo plano le ayudarán a escribir su propio procedimiento de exchange.

El `DoFieldExchange` función miembro es muy similar a la `Serialize` función miembro, es responsable de obtener o establecer datos hacia y desde un formulario externo (en este caso columnas del resultado de una consulta ODBC) desde y hacia los datos de miembro de la clase. El *pFX* parámetro es el contexto para el intercambio de datos y es similar a la *CArchive* parámetro `CObject::Serialize`. El *pFX* (un `CFieldExchange` objeto) tiene un indicador de operación, que es similar a, pero una generalización de la *CArchive* marca de dirección. Una función RFX que tenga que admiten las siguientes operaciones:

- `BindParam` Indicar el donde ODBC debe recuperar los datos del parámetro

- `BindFieldToColumn` : Indicar dónde ODBC debe recuperar/ingreso outputColumn datos

- `Fixup` : Establezca `CString/CByteArray` longitudes, establecer el estado NULL de bits

- `MarkForAddNew` : Marca con errores si el valor ha cambiado desde que llamar AddNew

- `MarkForUpdate` : Marca con errores si el valor ha cambiado desde que se llame la edición

- `Name` : Anexar los nombres de campo para los campos que se marquen como modificados

- `NameValue` : Anexar "\<nombre de columna > =" para los campos que se marquen como modificados

- `Value` : Anexe "" seguido de separador, al igual que ',' o ' '

- `SetFieldDirty` : Defina el campo de estado bit modificado (es decir, modificado)

- `SetFieldNull` : Establezca el bit de estado que indica un valor nulo para el campo

- `IsFieldDirty` : Devuelve el valor de bit de integridad de estado

- `IsFieldNull` : Devuelve el valor de bits de estado null

- `IsFieldNullable` : Devuelve TRUE si el campo puede contener valores NULL

- `StoreField` : El valor del campo de archivo

- `LoadField` : Volver a cargar el valor de campo archivados

- `GetFieldInfoValue` : Información general valor devuelto en un campo

- `GetFieldInfoOrdinal` : Información general valor devuelto en un campo

## <a name="user-extensions"></a>Extensiones de usuario

Hay varias maneras de extender el mecanismo predeterminado de RFX. Puede

- Agregar nuevos tipos de datos. Por ejemplo:

    ```cpp
    CBookmark
    ```

- Agregue nuevos procedimientos de exchange (RFX_).

    ```cpp
    void AFXAPI RFX_Bigint(CFieldExchange* pFX,
        const char *szName,
        BIGINT& value);
    ```

- Tiene la `DoFieldExchange` función miembro condicionalmente incluir llamadas adicionales de RFX o cualquier otra instrucción de C++ válido.

    ```cpp
    while (posExtraFields != NULL)
    {
        RFX_Text(pFX,
        m_listName.GetNext(posExtraFields),
        m_listValue.GetNext(posExtraValues));
    }
    ```

> [!NOTE]
> Dicho código ClassWizard no pueden editarlas y debe usarse solo fuera de los comentarios de formato especiales.

## <a name="writing-a-custom-rfx"></a>Escribir un RFX personalizado

Para escribir su propia función RFX personalizado, se recomienda que copie una función RFX existente y modificarlo para sus propios fines. Seleccionar el RFX derecho para copiar puede facilitar mucho más fácil el trabajo. Algunas funciones RFX tienen algunas propiedades únicas que debe tener en cuenta al decidir que se va a copiar.

`RFX_Long` y `RFX_Int`: Estas son las funciones de RFX más sencillas. El valor de datos no necesita ninguna interpretación especial y el tamaño de datos es fijo.

`RFX_Single` y `RFX_Double`: Al igual que RFX_Long y RFX_Int anterior, estas funciones son simples y puede hacer uso de la implementación predeterminada ampliamente. Se almacenan en dbflt.cpp en lugar de dbrfx.cpp, sin embargo, para habilitar la carga de la biblioteca de punto flotante solo cuando explícitamente se referencia en tiempo de ejecución.

`RFX_Text` y `RFX_Binary`: Estas dos funciones asignar previamente un búfer estático para contener la información de cadena o binarios y deben registrar estos búferes con ODBC SQLBindCol en lugar de registrar y valor. Por este motivo, estas dos funciones tienen una gran cantidad de código de casos especiales.

`RFX_Date`: ODBC devuelve información de fecha y hora en su propia estructura de datos TIMESTAMP_STRUCT. Esta función asigna dinámicamente un TIMESTAMP_STRUCT como un "proxy" para enviar y recibir datos en tiempo de fecha. Varias operaciones deben transferir la información de fecha y hora entre el C++ `CTime` objeto y el proxy TIMESTAMP_STRUCT. Esto complica considerablemente esta función, pero es un buen ejemplo de cómo usar a un proxy para la transferencia de datos.

`RFX_LongBinary`: Se trata de la biblioteca de clases solo función RFX que no utiliza el enlace de columna para recibir y enviar datos. Esta función pasa por alto la operación BindFieldToColumn y en su lugar, durante la operación de reparación, asigna almacenamiento para almacenar los datos entrantes SQL_LONGVARCHAR o SQL_LONGVARBINARY, a continuación, realiza una llamada SQLGetData para recuperar el valor en el almacenamiento asignado. Al prepararse para enviar los valores de datos de vuelta al origen de datos (por ejemplo, las operaciones de NameValue y valor), esta función utiliza la funcionalidad DATA_AT_EXEC de ODBC. Consulte [Nota técnica 45](../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md) para obtener más información sobre cómo trabajar con SQL_LONGVARBINARY y SQL_LONGVARCHARs.

Al escribir su propio **RFX_** función, a menudo podrá utilizar `CFieldExchange::Default` para implementar una operación determinada. Examine la implementación de forma predeterminada para la operación en cuestión. Si realiza la operación tendría que escribir su **RFX_** función se puede delegar en el `CFieldExchange::Default`. Puede ver ejemplos de llamada `CFieldExchange::Default` en dbrfx.cpp

Es importante llamar a `IsFieldType` al principio de la función RFX y devolver inmediatamente si devuelve FALSE. Este mecanismo mantiene las operaciones de parámetro se lleve a cabo en *outputColumns*y viceversa (como llamar a `BindParam` en un *outputColumn*). Además, `IsFieldType` automáticamente realiza un seguimiento del recuento de *outputColumns* (*m_nFields*) y params (*m_nParams*).

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
