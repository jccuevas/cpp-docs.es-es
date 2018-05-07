---
title: 'Tn045: compatibilidad MFC bases de datos con Long Varchar-varbinary | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.data
dev_langs:
- C++
helpviewer_keywords:
- TN045
- Varbinary data type
- Varchar data type
ms.assetid: cf572c35-5275-45b5-83df-5f0e36114f40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bd5201661afcdf6f4ae9676323f3f644817bcf7d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="tn045-mfcdatabase-support-for-long-varcharvarbinary"></a>TN045: Compatibilidad MFC/base de datos con Long Varchar/Varbinary
> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota describe cómo recuperar y enviar ODBC **SQL_LONGVARCHAR** y **SQL_LONGVARBINARY** clases de base de datos de tipos de datos mediante la MFC.  
  
## <a name="overview-of-long-varcharvarbinary-support"></a>Información general sobre la compatibilidad con Long Varchar/Varbinary  
 ODBC **SQL_LONG_VARCHAR** y **SQL_LONGBINARY** tipos de datos (denominados aquí como columnas de datos de tiempo) pueden contener grandes cantidades de datos. Existen 3 formas puede controlar estos datos:  
  
-   Enlazar a un `CString` / `CByteArray`.  
  
-   Enlazar a un `CLongBinary`.  
  
-   No enlácelo en absoluto y recuperar y enviar el valor de datos de tipo long manualmente, independiente de las clases de base de datos.  
  
 Cada uno de los tres métodos tiene ventajas y desventajas.  
  
 No se admiten columnas de datos de tipo Long para los parámetros a una consulta. Solo se admiten para outputColumns.  
  
## <a name="binding-a-long-data-column-to-a-cstringcbytearray"></a>Enlazar una columna de datos de tipo Long a un objeto CString/CByteArray  
 Ventajas:  
  
 Este enfoque es fácil de entender y trabajar con clases familiares. Proporciona el marco de trabajo `CFormView` compatibilidad con `CString` con `DDX_Text`. Tiene una gran cantidad de funcionalidad general de cadena o una colección con el `CString` y `CByteArray` clases y se puede controlar la cantidad de memoria asignada localmente para contener el valor de datos. El marco de trabajo mantiene una copia antigua de los datos de campo durante **editar** o `AddNew` las llamadas a funciones y lo puede framework detecta automáticamente los cambios en los datos de forma automática.  
  
> [!NOTE]
>  Puesto que `CString` está diseñado para trabajar en datos de caracteres, y `CByteArray` para trabajar en datos binarios, se recomienda colocar los datos de caracteres (**SQL_LONGVARCHAR**) en `CString`y los datos binarios ( **SQL_LONGVARBINARY**) en `CByteArray`.  
  
 El RFX funciones para `CString` y `CByteArray` tiene un argumento adicional que permite invalida el tamaño predeterminado de la memoria asignada para contener el valor recuperado de la columna de datos. Tenga en cuenta el argumento nMaxLength en las declaraciones de función siguientes:  
  
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
  
 Si recupera una columna de datos de tipo long en un `CString` o `CByteArray`, devuelto de la máxima cantidad de datos es, de forma predeterminada, 255 bytes. Se omite nada más allá de este. En este caso, el marco de trabajo producirá la excepción **AFX_SQL_ERROR_DATA_TRUNCATED**. Afortunadamente, es posible explícitamente aumentar nMaxLength para valores mayores, hasta **MAXINT**.  
  
> [!NOTE]
>  El valor de nMaxLength es usado por MFC para establecer el búfer local de la **SQLBindColumn** (función). Este es el búfer local para el almacenamiento de los datos y no afecta realmente la cantidad de datos devueltos por el controlador ODBC. `RFX_Text` y `RFX_Binary` solo realizar una llamada utilizando **SQLFetch** para recuperar los datos de la base de datos back-end. Cada controlador ODBC tiene una limitación diferentes en la cantidad de datos que se pueden devolver en una sola operación de obtención. Este límite puede ser mucho menor que el valor establecido en nMaxLength, en cuyo caso la excepción **AFX_SQL_ERROR_DATA_TRUNCATED** se iniciará. En estas circunstancias, pasar a utilizar `RFX_LongBinary` en lugar de `RFX_Text` o `RFX_Binary` para que se pueden recuperar todos los datos.  
  
 ClassWizard enlazará un **SQL_LONGVARCHAR** a una `CString`, o un **SQL_LONGVARBINARY** a un `CByteArray` para usted. Si desea asignar más de 255 bytes en la que recuperar la columna de datos de tipo long, a continuación, puede proporcionar un valor explícito para nMaxLength.  
  
 Cuando se enlaza una columna de datos de tipo long para una `CString` o `CByteArray`, actualizar el campo funciona igual que cuando se enlaza a un SQL_**VARCHAR** o SQL_**VARBINARY**. Durante la **editar**, se almacena en caché el valor de datos inmediatamente y versiones posteriores, en comparación con cuando **actualización** se llama para detectar cambios en los datos de valor y establecer el Dirty y valores Null para la columna de forma adecuada.  
  
## <a name="binding-a-long-data-column-to-a-clongbinary"></a>Enlazar una columna de datos de tipo Long a un objeto CLongBinary  
 Si la columna de datos de tipo long puede contener más **MAXINT** bytes de datos, probablemente le interesará recuperarla en una `CLongBinary`.  
  
 Ventajas:  
  
 Esta opción recupera una columna de datos long completo, hasta la memoria disponible.  
  
 Desventajas:  
  
 Los datos se mantienen en la memoria. Este método también resulta muy caro para grandes cantidades de datos. Debe llamar a `SetFieldDirty` para los datos enlazados miembro para garantizar el campo se incluye en un **actualización** operación.  
  
 Si se recuperan las columnas de datos de tipo long en un `CLongBinary`, las clases de base de datos se compruebe el tamaño total de la columna de datos de tipo long y asignar un `HGLOBAL` segmento de memoria lo suficientemente grande como para contener el valor de datos completo. Las clases de base de datos, a continuación, recuperar el valor de datos completa en asignada `HGLOBAL`.  
  
 Si el origen de datos no puede devolver el tamaño esperado de la columna de datos de tipo long, el marco de trabajo producirá la excepción **AFX_SQL_ERROR_SQL_NO_TOTAL**. Si el intento de asignar el `HGLOBAL` se produce un error, se produce una excepción de memoria estándar.  
  
 ClassWizard enlazará un **SQL_LONGVARCHAR** o **SQL_LONGVARBINARY** a un `CLongBinary` para usted. Seleccione `CLongBinary` como el tipo de Variable en el cuadro de diálogo Agregar variables miembro. ClassWizard, a continuación, agregará un `RFX_LongBinary` llamada a su `DoFieldExchange` llamar e incremente el número total de campos enlazados.  
  
 Para actualizar valores de la columna de datos long, primero asegúrese de que la asignada `HGLOBAL` es lo suficientemente grande como para contener los datos nuevos mediante una llamada a **:: GlobalSize** en el `m_hData` miembro de la `CLongBinary`. Si es demasiado pequeño, suelte el `HGLOBAL` y asignarle uno el tamaño adecuado. A continuación, establezca `m_dwDataLength` para reflejar el nuevo tamaño.  
  
 De lo contrario, si `m_dwDataLength` es mayor que el tamaño de los datos que va a sustituir, puede liberar y reasignar el `HGLOBAL`, o déjela en asignada. Asegúrese de que indican el número de bytes que se usa realmente en `m_dwDataLength`.  
  
## <a name="how-updating-a-clongbinary-works"></a>Cómo actualizar un CLongBinary funciona  
 No es necesario entender cómo actualizar un `CLongBinary` funciona, pero puede resultar útil como un ejemplo sobre cómo enviar valores de datos largos a un origen de datos, si elige este método tercera, se describe a continuación.  
  
> [!NOTE]
>  En orden para un `CLongBinary` campo se incluya en una actualización, debe llamar explícitamente a `SetFieldDirty` para el campo. Si realiza algún cambio en un campo, incluso si se establece en Null, debe llamar a `SetFieldDirty`. También debe llamar a `SetFieldNull`, con el segundo parámetro que se va a **FALSE**, para marcar el campo que tiene un valor.  
  
 Al actualizar una `CLongBinary` campo, utilizan de las clases de base de datos de ODBC **DATA_AT_EXEC** mecanismo (consulte la documentación de ODBC en **SQLSetPos**del argumento rgbValue). Cuando el marco de trabajo prepara la instrucción insert o update, en lugar de apuntar a la `HGLOBAL` que contiene los datos, el *dirección* de la `CLongBinary` se establece como el *valor* de la columna en su lugar y el conjunto de indicadores de longitud **SQL_DATA_AT_EXEC**. Posteriormente, cuando la instrucción update se envía al origen de datos, **SQLExecDirect** devolverá **SQL_NEED_DATA**. Esto le indica el marco de trabajo que el valor de los parámetros para esta columna es realmente la dirección de un `CLongBinary`. Las llamadas de framework **SQLGetData** una vez con un búfer pequeño, se espera el controlador para devolver la longitud real de los datos. Si el controlador devuelve la longitud real de los objetos binarios grandes (BLOB), MFC reasigna tanto espacio como sea necesario para capturar el BLOB. Si el origen de datos devuelve **SQL_NO_TOTAL**, que indica que no puede determinar el tamaño del BLOB, MFC creará bloques más pequeños. El tamaño inicial predeterminado es 64 KB y bloques subsiguientes será el doble del tamaño; Por ejemplo, el segundo elemento es 128 KB, el tercero es 256K y así sucesivamente. El tamaño inicial es configurable.  
  
## <a name="not-binding-retrievingsending-data-directly-from-odbc-with-sqlgetdata"></a>No enlace: Recuperar y enviar datos directamente desde ODBC con SQLGetData  
 Con este método completamente omitir las clases de base de datos y tratar con la columna de datos de tipo long.  
  
 Ventajas:  
  
 Puede almacenar en caché de disco si es necesario o decidir dinámicamente la cantidad de datos para recuperar datos.  
  
 Desventajas:  
  
 No obtendrá el marco de trabajo **editar** o `AddNew` soporte técnico, debe escribir código usted mismo para llevar a cabo la funcionalidad básica (**eliminar** funciona sin embargo, puesto que no es una operación de nivel de columna).  
  
 En este caso, la columna de datos de tipo long debe estar en la lista de selección del conjunto de registros, pero no se debe enlazar el marco de trabajo. Una manera de hacer esto consiste en proporcionar su propia instrucción SQL a través de `GetDefaultSQL` o como el argumento lpszSQL `CRecordset`del **abiertos** función y no enlazar la columna adicional con una llamada de función RFX_. ODBC requiere que los campos sin enlazar aparecen a la derecha de los campos enlazados, así que agregue las columnas o columna sin enlazar al final de la lista de selección.  
  
> [!NOTE]
>  Dado que la columna de datos de tipo long no está enlazada el marco de trabajo, no se controlarán los cambios en él con `CRecordset::Update` llamadas. Debe crear y enviar el código SQL necesario **insertar** y **actualización** instrucciones usted mismo.  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

