---
title: 'TN045: MFC-base de datos con Long Varchar / Varbinary'
ms.date: 11/04/2016
helpviewer_keywords:
- TN045
- Varbinary data type
- Varchar data type
ms.assetid: cf572c35-5275-45b5-83df-5f0e36114f40
ms.openlocfilehash: 3e8b356027e5c5b7c604a0354624d9f11e32fb9a
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611064"
---
# <a name="tn045-mfcdatabase-support-for-long-varcharvarbinary"></a>TN045: Compatibilidad de MFC/base de datos con Long Varchar/varbinary

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota describe cómo recuperar y enviar ODBC **SQL_LONGVARCHAR** y **SQL_LONGVARBINARY** las clases de base de datos de tipos de datos mediante MFC.

## <a name="overview-of-long-varcharvarbinary-support"></a>Información general de la compatibilidad con Long Varchar/Varbinary

ODBC **SQL_LONG_VARCHAR** y **SQL_LONGBINARY** tipos de datos (denominados aquí como columnas de datos long) pueden contener grandes cantidades de datos. Existen 3 formas de tratar estos datos:

- Enlazar a un `CString` / `CByteArray`.

- Enlazar a un `CLongBinary`.

- No enlazarlo en absoluto y recuperar y enviar el valor de datos de tipo long manualmente, independiente de las clases de base de datos.

Cada uno de los tres métodos tiene ventajas y desventajas.

No se admiten columnas de datos largos para los parámetros a una consulta. Solo se admiten para outputColumns.

## <a name="binding-a-long-data-column-to-a-cstringcbytearray"></a>Enlazar una columna de datos de tipo Long a un objeto CString/CByteArray

Ventajas:

Este enfoque es sencillo de entender y trabajar con clases familiares. Proporciona el marco de trabajo `CFormView` compatibilidad `CString` con `DDX_Text`. Tiene una gran cantidad de funcionalidad general de cadena o una colección con el `CString` y `CByteArray` clases y se puede controlar la cantidad de memoria asignada para contener el valor de datos. El marco de trabajo mantiene una copia antigua de los datos de campo durante `Edit` o `AddNew` llamadas de función y el framework se puede detectar automáticamente los cambios realizados en los datos por usted.

> [!NOTE]
>  Puesto que `CString` está diseñado para trabajar en los datos de caracteres, y `CByteArray` para trabajar en datos binarios, se recomienda colocar los datos de caracteres (**SQL_LONGVARCHAR**) en `CString`y los datos binarios ( **SQL_LONGVARBINARY**) en `CByteArray`.

El RFX funciones para `CString` y `CByteArray` tiene un argumento adicional que permite invalida el tamaño predeterminado de la memoria asignada para contener el valor recuperado de la columna de datos. Tenga en cuenta el argumento nMaxLength en las siguientes declaraciones de función:

```
void AFXAPI RFX_Text(CFieldExchange* pFX,
    const char *szName,
    CString& value,
    int nMaxLength = 255,
    int nColumnType =
    SQL_VARCHAR);

void AFXAPI RFX_Binary(CFieldExchange* pFX,
    const char *szName,
    CByteArray& value,
    int nMaxLength = 255);
```

Si recupera una columna de datos de tipo long en un `CString` o `CByteArray`, devuelve el máximo es la cantidad de datos, de forma predeterminada, 255 bytes. Se omite nada más allá de esto. En este caso, el marco de trabajo iniciará la excepción **AFX_SQL_ERROR_DATA_TRUNCATED**. Afortunadamente, puede explícitamente aumentar nMaxLength para valores mayores, hasta **MAXINT**.

> [!NOTE]
>  Se usa el valor de nMaxLength MFC para establecer el búfer local de la `SQLBindColumn` función. Este es el búfer local para el almacenamiento de los datos y no afecta realmente la cantidad de datos devueltos por el controlador ODBC. `RFX_Text` y `RFX_Binary` solo realizar una llamada con `SQLFetch` para recuperar los datos de la base de datos back-end. Cada controlador ODBC tiene una limitación diferentes en la cantidad de datos que se pueden devolver en una sola operación de obtención. Este límite puede ser mucho menor que el valor establecido en nMaxLength, en cuyo caso la excepción **AFX_SQL_ERROR_DATA_TRUNCATED** se iniciará. En estas circunstancias, pasar a usar `RFX_LongBinary` en lugar de `RFX_Text` o `RFX_Binary` para que se pueden recuperar todos los datos.

ClassWizard enlazará un **SQL_LONGVARCHAR** a un `CString`, o un **SQL_LONGVARBINARY** a un `CByteArray` para usted. Si desea asignar más de 255 bytes en la que se recupera de la columna de datos de tipo long, a continuación, puede proporcionar un valor explícito para nMaxLength.

Cuando se enlaza una columna de datos de tipo long para una `CString` o `CByteArray`, actualice el campo funciona exactamente igual que cuando se enlaza a un SQL_**VARCHAR** o SQL_**VARBINARY**. Durante la `Edit`, el valor de datos se almacena en caché inmediatamente y versiones posteriores, en comparación con cuando `Update` se llama para detectar cambios en los datos de valor y establecer el Dirty y valores Null para la columna de forma adecuada.

## <a name="binding-a-long-data-column-to-a-clongbinary"></a>Enlazar una columna de datos de tipo Long para un CLongBinary

Si la columna de datos long puede contener más **MAXINT** bytes de datos, probablemente le interesará recuperarla en una `CLongBinary`.

Ventajas:

Esto recupera una columna de datos long completo, hasta la memoria disponible.

Desventajas:

Los datos se mantienen en memoria. Este enfoque también es prohibitivo para grandes cantidades de datos. Debe llamar a `SetFieldDirty` para los datos enlazados miembro para asegurarse el campo se incluye en un `Update` operación.

Si se recuperan las columnas de datos de tipo long en un `CLongBinary`, compruebe el tamaño total de la columna de datos de tipo long las clases de base de datos y luego asignar un `HGLOBAL` segmento de memoria suficientemente grande como para contenga el valor de datos completo. Las clases de base de datos, a continuación, recuperar el valor de datos completa en asignada `HGLOBAL`.

Si el origen de datos no puede devolver el tamaño esperado de la columna de datos de tipo long, el marco de trabajo producirá la excepción **AFX_SQL_ERROR_SQL_NO_TOTAL**. Si el intento de asignar el `HGLOBAL` se produce un error, se produce una excepción de memoria estándar.

ClassWizard enlazará un **SQL_LONGVARCHAR** o **SQL_LONGVARBINARY** a un `CLongBinary` para usted. Seleccione `CLongBinary` como el tipo de Variable en el cuadro de diálogo Agregar variables miembro. ClassWizard, a continuación, agregará un `RFX_LongBinary` la llamada a su `DoFieldExchange` llamar e incremente el número total de campos enlazados.

Para actualizar los valores de columna de datos long, primero asegúrese de que la asignada `HGLOBAL` es lo suficientemente grande como para contener los datos nuevos mediante una llamada a **:: GlobalSize** en el *m_hData* miembro de la `CLongBinary`. Si es demasiado pequeño, suelte el `HGLOBAL` y asignar uno el tamaño adecuado. A continuación, establezca *m_dwDataLength* para reflejar el nuevo tamaño.

De lo contrario, si *m_dwDataLength* es mayor que el tamaño de los datos que se va a reemplazar, puede liberar y reasignar el `HGLOBAL`, o dejarla asignado. Asegúrese de indicar el número de bytes utilizados efectivamente en *m_dwDataLength*.

## <a name="how-updating-a-clongbinary-works"></a>Cómo actualizar un CLongBinary funciona

No es necesario entender cómo actualizar un `CLongBinary` funciona, pero puede resultar útil como un ejemplo sobre cómo enviar los valores de datos de tipo long para un origen de datos, si elige este método terceros, se describe a continuación.

> [!NOTE]
>  En orden para una `CLongBinary` campo que se incluirán en una actualización, debe llamar explícitamente a `SetFieldDirty` para el campo. Si realiza algún cambio en un campo, incluso si se establece en Null, debe llamar a `SetFieldDirty`. También debe llamar a `SetFieldNull`, siendo el segundo parámetro **FALSE**, para marcar el campo como si tuviera un valor.

Al actualizar un `CLongBinary` campo, las clases de base de datos usan de ODBC **DATA_AT_EXEC** mecanismo (consulte la documentación de ODBC en `SQLSetPos`del argumento rgbValue). Cuando el marco prepara la instrucción insert o update, en lugar de apuntar a la `HGLOBAL` que contiene los datos, el *dirección* de la `CLongBinary` se establece como el *valor* de la columna en su lugar y el conjunto de indicadores de longitud **SQL_DATA_AT_EXEC**. Posteriormente, cuando la instrucción update se envía al origen de datos, `SQLExecDirect` devolverá **SQL_NEED_DATA**. Esto le indica el marco de trabajo que el valor de los parámetros para esta columna es realmente la dirección de un `CLongBinary`. Las llamadas de framework `SQLGetData` una vez con un búfer pequeño, se espera el controlador para devolver la longitud real de los datos. Si el controlador devuelve la longitud real del objeto binario grande (BLOB), MFC reasigna tanto espacio como sea necesario para capturar el BLOB. Si el origen de datos devuelve **SQL_NO_TOTAL**, que indica que no puede determinar el tamaño del BLOB, MFC creará bloques más pequeños. El tamaño inicial predeterminado es 64 KB y bloques subsiguientes será el doble del tamaño; Por ejemplo, el segundo será 128K, el tercero es 256K y así sucesivamente. El tamaño inicial es configurable.

## <a name="not-binding-retrievingsending-data-directly-from-odbc-with-sqlgetdata"></a>No enlace: Recuperar y enviar datos directamente desde ODBC con SQLGetData

Con este método completamente omitir las clases de base de datos y tratar con la columna de datos de tipo long.

Ventajas:

Puede almacenar en caché datos de disco si es necesario decidir de forma dinámica la cantidad de datos para recuperar.

Desventajas:

No obtendrá el marco de trabajo `Edit` o `AddNew` soporte técnico y se debe escribir código para realizar funciones básicas (`Delete` funciona sin embargo, puesto que no es una operación de nivel de columna).

En este caso, la columna de datos de tipo long debe estar en la lista de selección del conjunto de registros, pero no se debería enlazar en el marco de trabajo. Una forma de hacerlo es proporcionar su propia instrucción SQL a través de `GetDefaultSQL` o como el argumento lpszSQL `CRecordset`del `Open` funcionar y no enlazar la columna adicional con una llamada de función RFX_. ODBC exige que aparecen sin enlazar campos a la derecha de los campos enlazados, por lo que agregar las columnas o columna sin enlazar al final de la lista de selección.

> [!NOTE]
>  Porque la columna de datos de tipo long no está enlazada el marco de trabajo, los cambios realizados en los no se controlará con `CRecordset::Update` llamadas. Debe crear y enviar la requiere SQL **insertar** y **actualización** instrucciones usted mismo.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
