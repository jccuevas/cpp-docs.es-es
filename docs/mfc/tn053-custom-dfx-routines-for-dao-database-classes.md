---
title: "TN053: Personalizar las rutinas DFX para las clases de base de datos DAO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.dfx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rutinas DFX personalizadas [C++]"
  - "DAO [C++], clases"
  - "DAO [C++], MFC"
  - "clases de base de datos [C++], DAO"
  - "DFX (intercambio de campos de registros DAO) [C++]"
  - "DFX (intercambio de campos de registros DAO) [C++], rutinas personalizadas"
  - "MFC [C++], DAO y"
  - "TN053"
ms.assetid: fdcf3c51-4fa8-4517-9222-58aaa4f25cac
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# TN053: Personalizar las rutinas DFX para las clases de base de datos DAO
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  A partir de Visual C\+\+ .NET, el entorno y los asistentes de Visual C\+\+ ya no admiten DAO \(aunque las clases DAO están incluidas y todavía puede utilizarlas\).  Microsoft recomienda utilizar [Plantillas OLE DB](../data/oledb/ole-db-templates.md) o [ODBC y MFC](../data/odbc/odbc-and-mfc.md) para nuevos proyectos.  Sólo debería utilizar DAO para mantener las aplicaciones existentes.  
  
 Esta nota técnica describe el mecanismo de intercambio de campos del registro de DAO \(DFX\).  Para ayudar a entender lo que está pasando en rutinas de DFX, la función de `DFX_Text` se explicará en detalle como ejemplo.  Como origen de información adicional a esta nota técnica, puede examinar el código para el otro funciones individuales DFX.  No es probable que necesite una rutina de custom DFX tan a menudo como podría necesitar una rutina de custom RFX \(utilizada con las clases de base de datos ODBC\).  
  
 Esta nota técnica contiene:  
  
-   Información general sobre DFX  
  
-   [Ejemplos](#_mfcnotes_tn053_examples) mediante el intercambio de registro de DAO y el enlace dinámico  
  
-   [Cómo funciona DFX](#_mfcnotes_tn053_how_dfx_works)  
  
-   [Qué hace la rutina de custom DFX](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)  
  
-   [Detalles de DFX\_Text](#_mfcnotes_tn053_details_of_dfx_text)  
  
 **Información general sobre DFX**  
  
 El mecanismo de intercambio de campos del registro de DAO \(DFX\) se utiliza para simplificar el procedimiento de recuperar y actualizar datos de utilizando la clase de `CDaoRecordset` .  El proceso se ha simplificado mediante los miembros de datos de clase de `CDaoRecordset` .  Derivando de `CDaoRecordset`, puede agregar los miembros de datos a la clase derivada que representa cada campo en una tabla o una consulta.  Este mecanismo “enlace estático” es simple, pero no puede ser la búsqueda de los datos y el método update de opción para todas las aplicaciones.  DFX recupera cada campo enlazado cada vez que se modifica el registro actual.  Si está desarrollando una aplicación rendimiento\- sensible que no requiere capturar cada campo cuando se cambia la divisa, “enlace dinámico” mediante `CDaoRecordset::GetFieldValue` y `CDaoRecordset::SetFieldValue` pueden ser el método de opción.  
  
> [!NOTE]
>  DFX y el enlace dinámico no son mutuamente excluyentes, por lo que un uso híbrido de static y el enlace dinámico se pueden utilizar.  
  
 **Ejemplo 1 \- uso de intercambio del registro de DAO sólo**  
  
 \(supone `CDaoRecordset` — clase derivada `CMySet` abierto\)  
  
```  
// Add a new record to the customers table  
myset.AddNew();  
myset.m_strCustID = _T("MSFT");  
myset.m_strCustName = _T("Microsoft");  
myset.Update();  
```  
  
 **Ejemplo 2 \- uso de enlaces dinámicos sólo**  
  
 \(supone mediante la clase de `CDaoRecordset` , `rs`, ya está abierto\)  
  
```  
// Add a new record to the customers table  
COleVariant  varFieldValue1 ( _T("MSFT"), VT_BSTRT );  
//Note: VT_BSTRT flags string type as ANSI, instead of UNICODE default  
COleVariant  varFieldValue2  (_T("Microsoft"), VT_BSTRT );  
rs.AddNew();  
rs.SetFieldValue(_T("Customer_ID"), varFieldValue1);  
rs.SetFieldValue(_T("Customer_Name"), varFieldValue2);  
rs.Update();  
```  
  
 **Ejemplo 3 \- uso de intercambio del registro de DAO y el enlace dinámico**  
  
 \(supone examinar los datos con `CDaoRecordset`\- clase derivada `emp`employee\)  
  
```  
// Get the employee's data so that it can be displayed  
emp.MoveNext();  
  
// If user wants to see employee's photograph,  
// fetch it  
COleVariant varPhoto;  
if (bSeePicture)  
   emp.GetFieldValue(_T("photo"), varPhoto);  
  
// Display the data  
PopUpEmployeeData(emp.m_strFirstName,  
    emp.m_strLastName, varPhoto);  
```  
  
 **Cómo funciona DFX**  
  
 El mecanismo de DFX funciona de forma similar al mecanismo de intercambio de campos de registros \(RFX\) utilizado por las clases ODBC de MFC.  Los principios de DFX y RFX son iguales pero hay diferencias internas numerosas.  El diseño de las funciones de DFX era tal que virtualmente todo el código es compartido por las rutinas individuales DFX.  En el DFX de nivel superior hace sólo algunas cosas.  
  
-   DFX construye la cláusula SQL **activada** y la cláusula SQL **PARÁMETROS** en caso necesario.  
  
-   DFX crea la estructura de enlace utilizada por la función de `GetRows` DAO \(más en esto más adelante\).  
  
-   DFX administra el búfer de datos utilizado para detectar campos modificados \(si se utiliza el doble\- búfer\)  
  
-   DFX administra las matrices de estado de **nulo** y de **SUCIO** y establece valores en caso necesario en actualizaciones.  
  
 En el núcleo del mecanismo de DFX es la función de `DoFieldExchange` de la clase derivada `CDaoRecordset` .  Esta función envía llamadas a funciones individuales DFX de un tipo adecuado de la operación.  Antes de llamar a `DoFieldExchange` las funciones internas de MFC establezca el tipo de la operación.  La lista siguiente muestra los diferentes tipos de la operación y una breve descripción.  
  
|Operación|Descripción|  
|---------------|-----------------|  
|**AddToParameterList**|Cláusula de los PARÁMETROS de compilaciones|  
|**AddToSelectList**|Las compilaciones SELECT la cláusula|  
|**BindField**|Configura la estructura de enlace|  
|**BindParam**|Establece los valores de parámetro|  
|**Corrección**|Establece el estado NULL|  
|**AllocCache**|Asigna la memoria caché para su comprobación modificada|  
|**StoreField**|Guarda el registro actual en caché|  
|**LoadField**|Restaura caché a los valores de miembro|  
|**FreeCache**|Libera memoria caché|  
|`SetFieldNull`|Establece el valor de & estado de campo en NULL|  
|**MarkForAddNew**|Marca los campos si no PSEUDO modificado NULL|  
|**MarkForEdit**|Marca los campos modificados si no coincide con la caché|  
|**SetDirtyField**|Establece los valores de campo marcados como modificados|  
  
 En la sección siguiente, cada operación se explicará más detalladamente para `DFX_Text`.  
  
 La característica más importante para entender el proceso de intercambio de campos del registro de DAO es que utiliza la función de `GetRows` del objeto de `CDaoRecordset` .  La función de DAO `GetRows` puede ser de varias maneras.  Esta nota técnica sólo describirá brevemente `GetRows` como está fuera del ámbito de esta nota técnica.  
  
 DAO `GetRows` puede ser de varias maneras.  
  
-   Puede capturar varios registros y varios campos de datos al mismo tiempo.  Esto permite un acceso a datos más rápido con la complicación de tratar con una estructura de datos grande y los desplazamientos correspondientes a cada campo y cada registro de datos en la estructura.  MFC no aprovecha este mecanismo de captura de registro múltiple.  
  
-   Otra manera en que `GetRows` puede trabajar es permitir que los desarrolladores especifican direcciones de enlace para los datos recuperados de cada campo de un registro de datos.  
  
-   DAO quiere también la “de nuevo la llamada” en el llamador para las columnas de longitud variable para permitir que el llamador asignar memoria.  Esta segunda característica tiene la ventaja de minimizar el número de copias de datos así como para permitir el almacenamiento directo de datos en los miembros de una clase \(la clase derivada de `CDaoRecordset` \).  El segundo mecanismo es el método MFC utiliza para enlazar a los miembros de datos en las clases derivadas de `CDaoRecordset` .  
  
##  <a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a> Qué hace la rutina de custom DFX  
 Resulta evidente de análisis que la operación más importante implementada en cualquier función de DFX debe ser la capacidad de configurar las estructuras de datos necesarias para llamar correctamente `GetRows`.  Hay otras operaciones que una función de DFX debe admitir también, pero ninguna tan importante o complejas como correctamente preparándose para la llamada de `GetRows` .  
  
 El uso de DFX se describe en la documentación en línea.  Esencialmente, hay dos requisitos.  Primero, los miembros se deben agregar a la clase derivada de `CDaoRecordset` para cada campo enlazado y parámetro.  Después de este `CDaoRecordset::DoFieldExchange` debe reemplazarse.  Observe que el tipo de datos de miembro es importante.  Debe coincidir con los datos del campo en la base de datos o al menos ser convertible a ese tipo.  Por ejemplo un campo numérico en base de datos, como un entero largo, se puede convertir siempre al texto y se enlaza a un miembro de `CString` , pero un campo de texto en una base de datos no se puede convertir necesariamente con una representación numérica, como integer y límite largos a un miembro entero largo.  DAO y el motor de base de datos Microsoft Jet son responsables de conversión \(en lugar de MFC\).  
  
##  <a name="_mfcnotes_tn053_details_of_dfx_text"></a> Detalles de DFX\_Text  
 Como se ha mencionado previamente, la mejor manera de explicar cómo funciona DFX es ejecutar un ejemplo.  Con este fin el pasar con los elementos internos quedan ocultos de `DFX_Text` debe funcionar bien para ayudar a proporcionar al menos un conocimiento básico de DFX.  
  
 **AddToParameterList**  
 Esta operación compila la cláusula SQL **PARÁMETROS** \(“`Parameters <param name>, <param type> ... ;`"\) necesaria para Jet.  Se denomina y se escribe cada parámetro \(como se especifica en la llamada RFX\).  Vea la función de **CDaoFieldExchange::AppendParamType** de función para ver los nombres de los tipos individuales.  En el caso de `DFX_Text`, el tipo utilizado es `text`.  
  
 **AddToSelectList**  
 Compila la cláusula SQL **activada** .  Esto es bastante sencillo como el nombre de columna especificado por la llamada de DFX se anexa simplemente \(“`SELECT <column name>, ...`"\).  
  
 **BindField**  
 El más complejo de operaciones.  Como se mencionó anteriormente es donde la estructura de enlace DAO utilizada por `GetRows` se configurar.  Como puede ver en `DFX_Text` los tipos de información de la estructura el tipo DAO utilizado \(**DAO\_CHAR** o **DAO\_WCHAR** en el caso de `DFX_Text`\).  Además, configurar el tipo de enlace utilizado también.  En una sección anterior `GetRows` se describe sólo brevemente, pero era suficiente explicar que el tipo de enlace utilizado por MFC siempre es enlace directa \(**DAOBINDING\_DIRECT**\).  Además del enlace de longitud variable de devolución de llamada del enlace de columna \(como `DFX_Text`\) se utiliza de forma que MFC puede controlar la asignación de memoria y especificar una dirección de longitud correcta.  Esto significa es el MFC puede indicar siempre DAO “where” colocar los datos, por lo que se pueden enlazar directamente a las variables miembro.  El resto de la estructura de enlace se completa con tareas como la dirección de la función de devolución de llamada de asignación de memoria y el tipo de enlace de la columna \(enlaces por columna nombre\).  
  
 **BindParam**  
 Ésta es una operación sencilla que llama a `SetParamValue` con el valor de parámetro especificado en el miembro del parámetro.  
  
 **Fixup**  
 Completa el estado de **nulo** para cada campo.  
  
 `SetFieldNull`  
 Esta operación marca sólo cada estado del campo como **nulo** y establece el valor de una variable miembro a **PSEUDO\_NULL**.  
  
 **SetDirtyField**  
 Llama a `SetFieldValue` para cada modificado como campo.  
  
 Todas las operaciones restantes tratan sólo de la caché de datos.  La caché de datos es un búfer adicional de los datos en el registro actual que se utiliza para crear algunas cosas más sencillas.  Por ejemplo, los campos “modificados” automáticamente pueden ser detectados.  Como se describe en la documentación en línea puede desactivar completamente o en el del terreno.  La implementación de búfer utiliza un mapa.  Esta asignación se utiliza para comparar en las copias asignadas dinámicamente de datos con la dirección de campo “límite” \(o el miembro derivado de los datos de `CDaoRecordset` \).  
  
 **AllocCache**  
 Asigna dinámicamente el valor de campo en caché y lo agrega al mapa.  
  
 **FreeCache**  
 Elimina el valor de campo almacenado en caché y lo quita del mapa.  
  
 **StoreField**  
 Copia el valor de campo actual en la caché de datos.  
  
 **LoadField**  
 Copia el valor almacenado en memoria caché en el miembro de campo.  
  
 **MarkForAddNew**  
 Comprueba si el valor de campo actual es**nulo** no y lo marca modificado en caso necesario.  
  
 **MarkForEdit**  
 El valor de campo actual con la caché de datos y marca modificado en caso necesario.  
  
> [!TIP]
>  Modele rutinas de custom DFX en rutinas existentes de DFX para los tipos de datos estándar.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)