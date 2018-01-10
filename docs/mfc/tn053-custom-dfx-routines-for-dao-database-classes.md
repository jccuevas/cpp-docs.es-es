---
title: 'TN053: Personalizar las rutinas DFX para DAO base de datos clases | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.dfx
dev_langs: C++
helpviewer_keywords:
- MFC, DAO and
- database classes [MFC], DAO
- DAO [MFC], MFC
- DFX (DAO record field exchange) [MFC], custom routines
- TN053
- DAO [MFC], classes
- DFX (DAO record field exchange) [MFC]
- custom DFX routines [MFC]
ms.assetid: fdcf3c51-4fa8-4517-9222-58aaa4f25cac
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c6935e4b3f2c8159677d1d322f6f875246160da2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>TN053: Personalizar las rutinas DFX para las clases de base de datos DAO
> [!NOTE]
>  El entorno de Visual C++ y los asistentes no admiten DAO (aunque las clases DAO están incluidas y puede seguir usándolos). Microsoft recomienda que utilice [plantillas OLE DB](../data/oledb/ole-db-templates.md) o [ODBC y MFC](../data/odbc/odbc-and-mfc.md) para los nuevos proyectos. Solo debería utilizar DAO para mantener las aplicaciones existentes.  
  
 Esta nota técnica describe el mecanismo de intercambio (DFX) de campos de registros DAO. Para ayudar a entender lo que sucede en las rutinas DFX, la `DFX_Text` función se explican detalladamente como ejemplo. Como una fuente de información para esta nota técnica adicional, puede examinar el código para los demás las funciones DFX individuales. Probablemente no necesitará una rutina DFX personalizada con tanta frecuencia como es posible que tenga una rutina RFX personalizada (usada con clases de base de datos ODBC).  
  
 Esta nota técnica contiene:  
  
-   Información general DFX  
  
- [Ejemplos](#_mfcnotes_tn053_examples) mediante el intercambio de campos de registros DAO y el enlace dinámico  
  
- [Cómo funciona DFX](#_mfcnotes_tn053_how_dfx_works)  
  
- [Lo que hace la rutina DFX personalizadas](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)  
  
- [Detalles de DFX_Text](#_mfcnotes_tn053_details_of_dfx_text)  
  
 **Información general DFX**  
  
 El mecanismo de intercambio de campos de registros DAO (DFX) se utiliza para simplificar el procedimiento de recuperación y actualización de datos cuando se usa el `CDaoRecordset` clase. El proceso se ha simplificado con miembros de datos de la `CDaoRecordset` clase. Al derivar de `CDaoRecordset`, puede agregar miembros de datos a la clase derivada que representa cada campo en una tabla o consulta. Este mecanismo de "enlace estático" es sencillo, pero puede que no sea el método de captura o de actualización de datos de elección para todas las aplicaciones. DFX recupera cada campo enlazado cada vez que cambia el registro actual. Si está desarrollando una aplicación de rendimiento es fundamental que no requiere que todos los campos de filas cuando se cambia la moneda, "enlace dinámico" a través de `CDaoRecordset::GetFieldValue` y `CDaoRecordset::SetFieldValue` puede ser el método de acceso de datos de elección.  
  
> [!NOTE]
>  DFX y la vinculación dinámica no son mutuamente excluyentes, por lo que puede utilizarse un uso híbrido de enlace estático y dinámico.  
  
## <a name="_mfcnotes_tn053_examples"></a>Ejemplo 1: Uso de intercambio de campos de registro DAO solo  
  
 (se da por supuesto `CDaoRecordset` : clase derivada `CMySet` está abierto)  
  
```  
// Add a new record to the customers table  
myset.AddNew();

myset.m_strCustID = _T("MSFT");

myset.m_strCustName = _T("Microsoft");

myset.Update();
```  
  
 **Ejemplo 2: Uso de solo un enlace dinámico**  
  
 (se supone usando `CDaoRecordset` (clase), `rs`, y ya está abierto)  
  
```  
// Add a new record to the customers table  
COleVariant  varFieldValue1 (_T("MSFT"),
    VT_BSTRT);

//Note: VT_BSTRT flags string type as ANSI,
    instead of UNICODE default  
COleVariant  varFieldValue2  (_T("Microsoft"),
    VT_BSTRT);

rs.AddNew();

rs.SetFieldValue(_T("Customer_ID"),
    varFieldValue1);

rs.SetFieldValue(_T("Customer_Name"),
    varFieldValue2);

rs.Update();
```  
  
 **Ejemplo 3: Uso de registro de intercambio de campos DAO y enlace dinámico**  
  
 (se da por supuesto examinan los datos empleados con `CDaoRecordset`-clase derivada `emp`)  
  
```  
// Get the employee's data so that it can be displayed  
emp.MoveNext();

 
// If user wants to see employee's photograph,  
// fetch it  
COleVariant varPhoto;  
if (bSeePicture)  
    emp.GetFieldValue(_T("photo"),
    varPhoto);

 
// Display the data  
PopUpEmployeeData(emp.m_strFirstName,  
    emp.m_strLastName,
    varPhoto);
```  
  
## <a name="_mfcnotes_tn053_how_dfx_works"></a>Cómo funciona DFX  
  
 El mecanismo DFX funciona de forma similar al mecanismo campos de registros (RFX) de exchange utilizado por las clases ODBC de MFC. Los principios de DFX y RFX son los mismos pero hay varias diferencias internas. El diseño de las funciones de DFX era tal que prácticamente todo el código se comparte por las rutinas DFX individuales. En sólo la DFX nivel más alto realiza algunas cosas.  
  
-   DFX construye el SQL **seleccione** cláusula y SQL **parámetros** cláusula si es necesario.  
  
-   DFX construye la estructura de enlace utilizada por de DAO `GetRows` función (más información sobre esto más adelante).  
  
-   DFX administra el búfer de datos que se utiliza para detectar los campos modificados (si se usa almacenamiento en búfer doble)  
  
-   DFX administra la **NULL** y **DIRTY** estado de las matrices y establece los valores si es necesario en las actualizaciones.  
  
 La esencia de la DFX mecanismo es el `CDaoRecordset` derivadas de la clase `DoFieldExchange` (función). Esta función envía llamadas a las funciones DFX individuales de un tipo de operación correspondiente. Antes de llamar a `DoFieldExchange` las funciones MFC internas establecen el tipo de operación. En la lista siguiente muestra los distintos tipos de operación y una breve descripción.  
  
|Operación|Descripción|  
|---------------|-----------------|  
|**AddToParameterList**|Cláusula de parámetros de compilaciones|  
|**AddToSelectList**|Cláusula SELECT de compilaciones|  
|**BindField**|Configura la estructura de enlace|  
|**BindParam**|Establece los valores de parámetro|  
|**Corrección**|Establece el estado NULL|  
|**AllocCache**|Asigna la memoria caché de comprobación de integridad|  
|**StoreField**|Guarda el registro actual en memoria caché|  
|**LoadField**|Restauraciones de caché para los valores de miembro|  
|**FreeCache**|Libera la memoria caché|  
|`SetFieldNull`|Conjuntos de campo Estado & valor en NULL|  
|**MarkForAddNew**|Campos de marcas desfasadas si no PSEUDO NULL|  
|**MarkForEdit**|If desfasada de campos de marcas no coinciden con la memoria caché|  
|**SetDirtyField**|Marcado con errores de valores de campo de conjuntos|  
  
 En la sección siguiente, cada operación se explican con más detalle para `DFX_Text`.  
  
 La característica más importante para comprender sobre el proceso de intercambio de campos de registros DAO radica en que usa el `GetRows` función de la `CDaoRecordset` objeto. DAO `GetRows` función puede trabajar de varias maneras. Esta nota técnica describirá brevemente `GetRows` porque está fuera del ámbito de esta nota técnica.  
  
 DAO `GetRows` puede trabajar de varias maneras.  
  
-   Pueden capturar varios registros y varios campos de datos al mismo tiempo. Esto permite obtener acceso a datos más rápido con la complicación de trabajar con una estructura de datos de gran tamaño y los desplazamientos correspondientes a cada campo y para cada registro de datos de la estructura. MFC no aprovechar las ventajas de este registro de varias filas mecanismo.  
  
-   Otra manera de `GetRows` puede trabajo consiste en permitir a los programadores especificar direcciones de enlace para los datos recuperados de cada campo de un registro de datos.  
  
-   DAO le también "devuelva la llamada" al autor de la llamada para las columnas de longitud variable para permitir que el llamador asignar memoria. Esta característica de segundo tiene la ventaja de minimizando el número de copias de datos, así como para permitir el almacenamiento directo de datos en los miembros de una clase (el `CDaoRecordset` clase derivada). Este segundo mecanismo es el método de MFC utiliza para enlazar a los miembros de datos en `CDaoRecordset` las clases derivadas.  
  
##  <a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a>Lo que hace la rutina DFX personalizadas  
 Es evidente de esta explicación que la operación más importante que se implementa en las funciones DFX debe ser la capacidad de configurar las estructuras de datos necesarios para llamar correctamente a `GetRows`. Hay una serie de otras operaciones debe ser compatible también con una función DFX, pero ninguna como importantes o complejos como preparar correctamente la `GetRows` llamar.  
  
 El uso de DFX se describe en la documentación en línea. Básicamente, hay dos requisitos. En primer lugar, los miembros deben agregarse a la `CDaoRecordset` clase derivada para cada parámetro y campo vinculado. A continuación `CDaoRecordset::DoFieldExchange` debe reemplazarse. Tenga en cuenta que el tipo de datos del miembro es importante. Debe coincidir con los datos del campo en la base de datos o al menos ser convertible a ese tipo. Por ejemplo, un campo numérico en la base de datos, como un entero largo, siempre se convertidos a texto y enlazado a un `CString` miembro, pero un campo de texto en una base de datos no necesariamente se puede convertir en una representación numérica, como entero largo y enlazado a un integ largo ER miembro. DAO y del motor de base de datos de Microsoft Jet son responsables de la conversión (en lugar de MFC).  
  
##  <a name="_mfcnotes_tn053_details_of_dfx_text"></a>Detalles de DFX_Text  
 Como se mencionó anteriormente, la mejor manera para explicar cómo funciona DFX es para que funcione a través de un ejemplo. Para este propósito que pasar por el funcionamiento interno de `DFX_Text` debería funcionar muy bien para ayudar a proporcionar al menos un conocimiento básico de DFX.  
  
 **AddToParameterList**  
 Esta operación genera el código SQL **parámetros** cláusula ("`Parameters <param name>, <param type> ... ;`") requiere Jet. Cada parámetro denominado y escrito (tal y como se especifica en la llamada RFX). Vea la función **CDaoFieldExchange::AppendParamType** función para ver los nombres de los tipos individuales. En el caso de `DFX_Text`, el tipo utilizado es `text`.  
  
 **AddToSelectList**  
 Compila el código SQL **seleccione** cláusula. Esto es bastante sencilla como el nombre de columna especificado por la llamada DFX es simplemente anexa ("`SELECT <column name>, ...`").  
  
 **BindField**  
 La más compleja de las operaciones. Como se mencionó anteriormente es que la estructura de enlace de DAO utilizado por `GetRows` está configurado. Como puede ver desde el código en `DFX_Text` los tipos de información en la estructura de incluyen el tipo DAO utilizado (**DAO_CHAR** o **DAO_WCHAR** en el caso de `DFX_Text`). Además, también se establece el tipo de enlace que se usa. En una sección anterior `GetRows` se describen brevemente, pero es suficiente explicar que el tipo de enlace utilizado por MFC siempre es el enlace de dirección directa (**DAOBINDING_DIRECT**). Además, para el enlace de columna de longitud variable (como `DFX_Text`) se usa el enlace de devolución de llamada para que MFC puede controlar la asignación de memoria y se especifica una dirección de la longitud correcta. Esto significa que MFC siempre puede deducir DAO "where" poner los datos, lo que permite el enlace directamente a las variables de miembro. El resto de la estructura de enlace se rellena con elementos tales como la dirección de la función de devolución de llamada de asignación de memoria y el tipo de enlace de columna (enlace por nombre de columna).  
  
 **BindParam**  
 Se trata de una operación simple que llama `SetParamValue` con el valor del parámetro especificado en el miembro de parámetro.  
  
 **Corrección**  
 Rellene la **NULL** estado para cada campo.  
  
 `SetFieldNull`  
 Esta operación solo marca el estado de cada campo como **NULL** y establece el miembro de valor de la variable en **PSEUDO_NULL**.  
  
 **SetDirtyField**  
 Llamadas `SetFieldValue` para cada campo marcados como modificado.  
  
 Todas las operaciones restantes solo tratan con el uso de la caché de datos. La caché de datos es un búfer adicional de los datos en el registro actual que se utiliza para realizar ciertas cosas más sencilla. Por ejemplo, pueden detectar automáticamente los campos "sucios". Como se describe en la documentación en línea que se puede desactivar completamente o en el nivel de campo. La implementación del búfer utiliza una asignación. Esta asignación se utiliza para hacer coincidir los asignada dinámicamente copias de los datos con la dirección del campo "enlazado" (o `CDaoRecordset` derivados de miembro de datos).  
  
 **AllocCache**  
 Asigna el valor del campo en caché y lo agrega a la asignación dinámicamente.  
  
 **FreeCache**  
 Elimina el valor del campo en caché y lo quita de la asignación.  
  
 **StoreField**  
 Copia el valor del campo actual en la caché de datos.  
  
 **LoadField**  
 Copia el valor almacenado en caché en el miembro de campo.  
  
 **MarkForAddNew**  
 Comprueba si es el valor actual del campo no es**NULL** y lo marca desfasadas si es necesario.  
  
 **MarkForEdit**  
 Compara el valor actual del campo con la memoria caché de datos y las marca desfasadas si es necesario.  
  
> [!TIP]
>  Modelo rutinas DFX personalizadas en las rutinas DFX existentes para los tipos de datos estándar.  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

