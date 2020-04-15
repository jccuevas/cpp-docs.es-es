---
title: 'TN045: Compatibilidad con bases de datos MFC para varchar-Varbinary largo'
ms.date: 11/04/2016
helpviewer_keywords:
- TN045
- Varbinary data type
- Varchar data type
ms.assetid: cf572c35-5275-45b5-83df-5f0e36114f40
ms.openlocfilehash: f67d159fb600dcacd8eedd40e672edf18bddee9a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365510"
---
# <a name="tn045-mfcdatabase-support-for-long-varcharvarbinary"></a>TN045: Compatibilidad MFC/base de datos con Long Varchar/Varbinary

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota describe cómo recuperar y enviar los tipos de datos **ODBC SQL_LONGVARCHAR** y **SQL_LONGVARBINARY** mediante las clases de base de datos MFC.

## <a name="overview-of-long-varcharvarbinary-support"></a>Descripción general del soporte de Long Varchar/Varbinary

El **SQL_LONG_VARCHAR** ODBC y los tipos de datos **SQL_LONGBINARY** (denominados aquí como columnas de datos largos) pueden contener grandes cantidades de datos. Hay 3 maneras de manejar estos datos:

- Enlazarlo a `CString` / `CByteArray`un archivo .

- Enlazarlo a `CLongBinary`un archivo .

- No lo enlace en absoluto y recupere y envíe el valor de datos largos manualmente, independientemente de las clases de base de datos.

Cada uno de los tres métodos tiene ventajas y desventajas.

Las columnas de datos largas no se admiten para los parámetros de una consulta. Solo se admiten para outputColumns.

## <a name="binding-a-long-data-column-to-a-cstringcbytearray"></a>Enlazar una columna de datos larga a un CString/CByteArray

Ventajas:

Este enfoque es fácil de entender y se trabaja con clases familiares. El marco `CFormView` de `CString` `DDX_Text`trabajo proporciona compatibilidad con . Tiene una gran cantidad de cadena `CString` general `CByteArray` o funcionalidad de recopilación con las clases y, y puede controlar la cantidad de memoria asignada localmente para contener el valor de datos. El marco de trabajo mantiene una `Edit` `AddNew` copia antigua de los datos de campo durante o las llamadas de función, y el marco de trabajo puede detectar automáticamente los cambios en los datos por usted.

> [!NOTE]
> Puesto `CString` que está diseñado para `CByteArray` trabajar en datos de caracteres y para trabajar en `CString`datos binarios, se recomienda colocar los datos de caracteres (**SQL_LONGVARCHAR**) en , y los datos binarios (**SQL_LONGVARBINARY**) en `CByteArray`.

Las funciones `CString` RFX para y `CByteArray` tienen un argumento adicional que le permite invalidar el tamaño predeterminado de la memoria asignada para contener el valor recuperado para la columna de datos. Observe el argumento nMaxLength en las siguientes declaraciones de función:

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

Si recupera una columna de `CString` `CByteArray`datos larga en un o , la cantidad máxima de datos devuelta es, de forma predeterminada, 255 bytes. Cualquier cosa más allá de esto se ignora. En este caso, el marco de trabajo producirá la excepción **AFX_SQL_ERROR_DATA_TRUNCATED**. Afortunadamente, puede aumentar explícitamente nMaxLength a valores mayores, hasta **MAXINT**.

> [!NOTE]
> MFC utiliza el valor de nMaxLength para establecer `SQLBindColumn` el búfer local de la función. Este es el búfer local para el almacenamiento de los datos y en realidad no afecta a la cantidad de datos devueltos por el controlador ODBC. `RFX_Text`y `RFX_Binary` solo realizar `SQLFetch` una llamada utilizando para recuperar los datos de la base de datos back-end. Cada controlador ODBC tiene una limitación diferente en la cantidad de datos que pueden devolver en una sola captura. Este límite puede ser mucho menor que el valor establecido en nMaxLength, en cuyo caso se producirá la excepción **AFX_SQL_ERROR_DATA_TRUNCATED.** En estas circunstancias, `RFX_LongBinary` cambie `RFX_Text` a `RFX_Binary` using en lugar de o para que se puedan recuperar todos los datos.

ClassWizard enlazará **SQL_LONGVARCHAR** un `CString`SQL_LONGVARCHAR a un `CByteArray` , o un **SQL_LONGVARBINARY** a para usted. Si desea asignar más de 255 bytes en los que recupera la columna de datos largos, puede proporcionar un valor explícito para nMaxLength.

Cuando una columna de datos `CString` `CByteArray`larga está enlazada a un o , actualizar el campo funciona igual que cuando está enlazado a una SQL_**VARCHAR** o SQL_**VARBINARY**. Durante `Edit`, el valor de datos `Update` se almacena en caché y se compara más adelante cuando se llama para detectar cambios en el valor de datos y establecer los valores Dirty y Null para la columna de forma adecuada.

## <a name="binding-a-long-data-column-to-a-clongbinary"></a>Enlazar una columna de datos larga a un CLongBinary

Si la columna de datos larga puede contener más bytes **MAXINT** `CLongBinary`de datos, probablemente debería considerar recuperarlos en un archivo .

Ventajas:

Esto recupera toda una columna de datos larga, hasta la memoria disponible.

Desventajas:

Los datos se mantienen en la memoria. Este enfoque también es prohibitivamente costoso para grandes cantidades de datos. Debe llamar `SetFieldDirty` al miembro de datos enlazado para `Update` asegurarse de que el campo se incluye en una operación.

Si recupera columnas de `CLongBinary`datos largas en un , las clases de `HGLOBAL` base de datos comprobarán el tamaño total de la columna de datos larga y, a continuación, asignarán un segmento de memoria lo suficientemente grande como para contener todo el valor de datos. A continuación, las clases de `HGLOBAL`base de datos recuperan todo el valor de datos en el archivo .

Si el origen de datos no puede devolver el tamaño esperado de la columna de datos larga, el marco de trabajo producirá la excepción **AFX_SQL_ERROR_SQL_NO_TOTAL**. Si se produce `HGLOBAL` un error en el intento de asignar el error, se produce una excepción de memoria estándar.

ClassWizard enlazará un **SQL_LONGVARCHAR** `CLongBinary` o **SQL_LONGVARBINARY** a un para usted. Seleccione `CLongBinary` como Tipo de variable en el cuadro de diálogo Agregar variable miembro. ClassWizard agregará una `RFX_LongBinary` llamada `DoFieldExchange` a la llamada e incrementará el número total de campos enlazados.

Para actualizar los valores de columna `HGLOBAL` de datos largos, primero asegúrese de que el asignado `CLongBinary`es lo suficientemente grande como para contener los nuevos datos llamando a **::GlobalSize** en el *m_hData* miembro del archivo . Si es demasiado pequeño, `HGLOBAL` suelte el y asigne uno del tamaño adecuado. A continuación, establezca *m_dwDataLength* para reflejar el nuevo tamaño.

De lo contrario, si *m_dwDataLength* es mayor que el tamaño de los datos `HGLOBAL`que va a reemplazar, puede liberar y reasignar el , o dejarlo asignado. Asegúrese de indicar el número de bytes realmente utilizados en *m_dwDataLength*.

## <a name="how-updating-a-clongbinary-works"></a>Cómo funciona la actualización de un CLongBinary

No es necesario comprender cómo `CLongBinary` funciona la actualización de un trabajo, pero puede ser útil como ejemplo sobre cómo enviar valores de datos largos a un origen de datos, si elige este tercer método, que se describe a continuación.

> [!NOTE]
> Para que `CLongBinary` un campo se incluya en una actualización, debe llamar `SetFieldDirty` explícitamente al campo. Si realiza algún cambio en un campo, incluido `SetFieldDirty`el establecimiento Null, debe llamar a . También debe `SetFieldNull`llamar a , con el segundo parámetro false **,** para marcar el campo como que tiene un valor.

Al actualizar `CLongBinary` un campo, las clases de base de `SQLSetPos`datos utilizan el mecanismo de **DATA_AT_EXEC** de ODBC (consulte la documentación de ODBC sobre el argumento rgbValue de 's). Cuando el marco de trabajo prepara la instrucción `HGLOBAL` insert o update, `CLongBinary` en lugar de apuntar a los datos que contienen, la *dirección* de la se establece como el *valor* de la columna en su lugar, y el indicador de longitud establecido en **SQL_DATA_AT_EXEC**. Más adelante, cuando la instrucción update `SQLExecDirect` se envía al origen de datos, se devolverá **SQL_NEED_DATA**. Esto alerta al marco de trabajo de que el valor `CLongBinary`del parámetro para esta columna es realmente la dirección de un archivo . El marco `SQLGetData` de trabajo llama una vez con un búfer pequeño, esperando que el controlador devuelva la longitud real de los datos. Si el controlador devuelve la longitud real del objeto binario grande (el BLOB), MFC reasigna tanto espacio como sea necesario para capturar el BLOB. Si el origen de datos devuelve **SQL_NO_TOTAL**, lo que indica que no puede determinar el tamaño del BLOB, MFC creará bloques más pequeños. El tamaño inicial predeterminado es 64K, y los bloques subsiguientes serán el doble del tamaño; por ejemplo, el segundo será 128K, el tercero es 256K, y así sucesivamente. El tamaño inicial es configurable.

## <a name="not-binding-retrievingsending-data-directly-from-odbc-with-sqlgetdata"></a>No enlace: recuperar/enviar datos directamente desde ODBC con SQLGetData

Con este método se omiten completamente las clases de base de datos y se ocupan de la columna de datos larga usted mismo.

Ventajas:

Puede almacenar en caché los datos en el disco si es necesario o decidir dinámicamente cuántos datos recuperar.

Desventajas:

No obtiene el marco `Edit` de `AddNew` trabajo o la compatibilidad, y debe escribir`Delete` código usted mismo para realizar la funcionalidad básica (funciona, sin embargo, ya que no es una operación de nivel de columna).

En este caso, la columna de datos larga debe estar en la lista de selección del conjunto de registros, pero no debe estar enlazada por el marco de trabajo. Una forma de hacerlo es proporcionar su `GetDefaultSQL` propia instrucción SQL a `CRecordset`través o como el argumento lpszSQL a la función 's `Open` y no enlazar la columna adicional con una llamada de función RFX_. ODBC requiere que los campos sin enlazar aparezcan a la derecha de los campos enlazados, por lo que debe agregar la columna o columnas sin enlazar al final de la lista de selección.

> [!NOTE]
> Dado que la columna de datos larga no está enlazada `CRecordset::Update` por el marco de trabajo, los cambios en ella no se controlarán con llamadas. Debe crear y enviar las instrucciones SQL **INSERT** y **UPDATE** necesarias usted mismo.

## <a name="see-also"></a>Consulte también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
