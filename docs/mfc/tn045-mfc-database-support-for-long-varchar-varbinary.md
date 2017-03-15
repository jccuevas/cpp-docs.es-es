---
title: "TN045: Compatibilidad MFC/base de datos con Long Varchar/Varbinary | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TN045"
  - "Varbinary (tipo de datos)"
  - "Varchar (tipo de datos)"
ms.assetid: cf572c35-5275-45b5-83df-5f0e36114f40
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# TN045: Compatibilidad MFC/base de datos con Long Varchar/Varbinary
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea.  Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos.  Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota describe cómo recuperar y enviar los tipos de datos de ODBC **SQL\_LONGVARCHAR** y de **SQL\_LONGVARBINARY** mediante las clases de base de datos MFC.  
  
## Información general de compatibilidad Long Varchar\/Varbinary  
 Los tipos de datos de ODBC **SQL\_LONG\_VARCHAR** y de **SQL\_LONGBINARY** \(denominados aquí columnas de datos long\) pueden contener enormes cantidades de datos.  Hay 3 maneras que puede controlar estos datos:  
  
-   Enlácelo a `CString`\/`CByteArray`.  
  
-   Enlácelo a `CLongBinary`.  
  
-   No lo enlace en absoluto y no recupere y no envía el valor de datos largo manualmente, independientemente de las clases de base de datos.  
  
 Cada uno de los tres métodos tiene ventajas y desventajas.  
  
 Las columnas de datos que no se admiten para los parámetros a una consulta.  Solo se admiten para los outputColumns.  
  
## Enlazar una columna de datos Long a un CString\/CByteArray  
 Ventajas:  
  
 Este enfoque es simple entender, y trabaja con clases familiares.  El marco de trabajo proporciona compatibilidad de `CFormView` para `CString` con `DDX_Text`.  Tiene muchos de funcionalidad general de la cadena o de la colección con las clases de `CString` y de `CByteArray` , y puede controlar la cantidad de memoria asignada localmente para contener el valor de datos.  El marco mantiene una copia antigua de datos de campo durante **edición** o llamadas de función `AddNew` , y el marco puede automáticamente detectar cambios en los datos.  
  
> [!NOTE]
>  Puesto que `CString` está diseñado para funcionar en datos de caracteres, y `CByteArray` para trabajar en datos binarios, se recomienda colocar los datos de caracteres \(**SQL\_LONGVARCHAR**\) en `CString`, y los datos binarios \(**SQL\_LONGVARBINARY**\) en `CByteArray`.  
  
 Las funciones RFX para `CString` y `CByteArray` tienen un argumento adicional que le permite invalidar el tamaño predeterminado de la memoria asignada para contener el valor recuperado de la columna de datos.  Observe el argumento nMaxLength en las declaraciones de función siguientes:  
  
```  
void AFXAPI RFX_Text(CFieldExchange* pFX, const char *szName,  
    CString& value, int nMaxLength = 255, int nColumnType =  
    SQL_VARCHAR);  
  
void AFXAPI RFX_Binary(CFieldExchange* pFX, const char *szName,   
    CByteArray& value,int nMaxLength = 255);  
```  
  
 Si recupera una columna de datos larga en `CString` o `CByteArray`, la cantidad devuelto máximo de datos es, de forma predeterminada, 255 bytes.  Nada más allá de esto se omite.  En este caso, el marco producirá una excepción **AFX\_SQL\_ERROR\_DATA\_TRUNCATED**.  Afortunadamente, puede explícitamente aumentar el nMaxLength a valores mayores, hasta **MAXINT**.  
  
> [!NOTE]
>  El valor de nMaxLength utiliza MFC para establecer el búfer local de la función de **SQLBindColumn** .  Este es el búfer local para el almacenamiento de datos y no afecta a la cantidad de datos devueltos por el controlador ODBC.  `RFX_Text` y `RFX_Binary` haga solo una llamada mediante **SQLFetch** para recuperar los datos de la base de datos back\-end.  Cada controlador ODBC tiene otra limitación en la cantidad de datos que se pueden devolver en una única búsqueda.  Este límite puede ser mucho menor que el valor establecido en nMaxLength, en cuyo caso la excepción **AFX\_SQL\_ERROR\_DATA\_TRUNCATED** produce.  En estas circunstancias, cambie a utilizar `RFX_LongBinary` en lugar de `RFX_Text` o de `RFX_Binary` para poder recuperar todos los datos.  
  
 ClassWizard enlazará **SQL\_LONGVARCHAR** a `CString`, o **SQL\_LONGVARBINARY** a `CByteArray` automáticamente.  Si desea asignar más de 255 bytes en los que se recupere la columna de datos larga, puede proporcionar un valor explícito para el nMaxLength.  
  
 Cuando una columna de datos larga se enlaza a `CString` o a `CByteArray`, actualizar el terreno trabajo en exactamente igual que cuando se enlaza a un SQL\_**VARCHAR** o a SQL\_**VARBINARY**.  Durante **edición**, el valor de datos se almacena en caché lejos y se compara posteriormente cuando **Actualización** se denomina para detectar cambios en el valor de los datos y establecer el modificado y valores NULL para la columna correctamente.  
  
## Enlazar una columna de datos Long un CLongBinary  
 Si la columna de datos larga puede contener más bytes de **MAXINT** de datos, debe considerar probablemente recuperarlos en `CLongBinary`.  
  
 Ventajas:  
  
 Esto recupera una columna de datos larga completa, hasta la memoria disponible.  
  
 Desventajas:  
  
 Los datos se mantiene en la memoria.  Este enfoque también es prohibitivo costoso para grandes cantidades de datos.  Debe llamar a `SetFieldDirty` para que el miembro enlazado a datos asegure el campo se incluye en una operación de **Actualización** .  
  
 Si recupera columnas de datos largas en `CLongBinary`, las clases de base de datos comprobará el tamaño total de la columna de datos larga, se asignan un segmento de memoria de `HGLOBAL` suficientemente grande para llevarlo a cabo el valor de datos completo.  Las clases de base de datos a continuación recupera el valor de datos completo en `HGLOBAL`asignado.  
  
 Si el origen de datos no puede devolver el tamaño esperado de la columna de datos larga, el marco producirá una excepción **AFX\_SQL\_ERROR\_SQL\_NO\_TOTAL**.  Si se produce un error en el intento de asignar `HGLOBAL` , se produce una excepción estándar de memoria.  
  
 ClassWizard enlazará **SQL\_LONGVARCHAR** o **SQL\_LONGVARBINARY** a `CLongBinary` automáticamente.  `CLongBinary` seleccione como la variable escriba en el cuadro de diálogo para agregar variables miembro.  ClassWizard después agregará una llamada de `RFX_LongBinary` a la llamada de `DoFieldExchange` y aumentará el número total de campos enlazados.  
  
 Para actualizar valores largos de la columna de datos, asegúrese primero de que `HGLOBAL` asignado es bastante grande para contener los nuevos datos llamando a **::GlobalSize** en el miembro de `m_hData` de `CLongBinary`.  Si es demasiado pequeño, suelte `HGLOBAL` y asigna uno el tamaño adecuado.  `m_dwDataLength` establezca para reflejar el nuevo tamaño.  
  
 Si no, si `m_dwDataLength` es mayor que el tamaño de los datos que reemplaza, puede o liberar y reasignar `HGLOBAL`, o déjelo asignado.  Asegúrese de indicar el número de bytes utilizados realmente en `m_dwDataLength`.  
  
## Cómo funciona actualizar un CLongBinary  
 No es necesario conocer cómo funciona actualizar `CLongBinary` , pero puede ser útil como un ejemplo de cómo enviar valores de datos largos a un origen de datos, si elige este tercer método, se describe más adelante.  
  
> [!NOTE]
>  Para que un campo de `CLongBinary` se incluya en una actualización, debe llamar explícitamente a `SetFieldDirty` para el campo.  Si realiza algún cambio en un campo, incluidos establecerlo Null, se debe llamar a `SetFieldDirty`.  También debe llamar a `SetFieldNull`, con el segundo parámetro siendo **FALSE**, para marcar el campo como si un valor.  
  
 Al actualizar un campo de `CLongBinary` , el mecanismo de **DATA\_AT\_EXEC** de ODBC de uso de las clases de base de datos \(vea la documentación de ODBC en el argumento de rgbValue de **SQLSetPos** \).  Cuando el marco prepara la inserción o instrucción de actualización, en lugar de indicar a `HGLOBAL` que contiene datos, *la dirección* de `CLongBinary` se establece como *el valor* de la columna en su lugar, y el indicador de longitud establecido en **SQL\_DATA\_AT\_EXEC**.  Más adelante, cuando la instrucción de actualización se envía al origen de datos, **SQLExecDirect** devolverá **SQL\_NEED\_DATA**.  Esto avisa el marco que el valor de parámetros para esta columna es realmente la dirección de `CLongBinary`.  El marco de trabajo llama a **SQLGetData** una vez con un pequeño búfer, espera que el controlador devuelve la longitud real de los datos.  Si el controlador devuelve la longitud real del objeto binario grande \(BLOB\), MFC reasigna tanto espacio como sea necesario para capturar BLOB.  Si el origen de datos devuelve **SQL\_NO\_TOTAL**, lo que indica que no puede determinar el tamaño del BLOB, MFC creará bloques menores.  El tamaño inicial predeterminado es de, y los bloques posteriores se el tamaño doble; por ejemplo, el segundo se 128K, el tercero es 256K, etc.  El tamaño inicial es configurable.  
  
## No enlazar: El recupera\/datos Directamente de Sending de ODBC con SQLGetData  
 Con este método se omite completamente las clases de base de datos, y tratamiento a la columna de datos larga personalmente.  
  
 Ventajas:  
  
 Puede almacenar en caché datos en disco en caso necesario, o decida dinámicamente cuántos datos a recuperar.  
  
 Desventajas:  
  
 No obtiene **edición** de marco o `AddNew` admite, y debe escribir código a para realizar funcionalidad básica \(**Suprimir** funciona sin embargo, puesto que no es una operación de nivel de columna\).  
  
 En este caso, la columna de datos larga debe estar en la lista de selección de conjunto de registros, pero no se debe enlazar el marco.  Una manera de hacerlo es proporcionar dispone de la instrucción SQL mediante `GetDefaultSQL` o como argumento lpszSQL a la función de `CRecordset`**Abierta** , y no enlazar la columna adicional con una llamada de función de RFX\_.  ODBC requiere que los campos independientes aparecen a la derecha de los campos enlazados, lo que agrega la columna o columnas sin enlazar al final de la lista de selección.  
  
> [!NOTE]
>  Dado que la columna de datos larga no está enlazado por el marco, los cambios no se administran con las llamadas de `CRecordset::Update` .  Debe crear y enviar SQL necesario **INSERT** e instrucciones de **ACTUALIZACIÓN** personalmente.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)