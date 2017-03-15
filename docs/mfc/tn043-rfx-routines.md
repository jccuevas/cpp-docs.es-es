---
title: "TN043: Rutinas RFX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RFX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RFX (intercambio de campos de registros)"
  - "RFX (intercambio de campos de registros), arquitectura"
  - "TN043"
ms.assetid: f552d0c1-2c83-4389-b472-42c9940aa713
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# TN043: Rutinas RFX
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea.  Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos.  Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota describe la arquitectura de intercambio de campos de registros.  También describe cómo escribe un procedimiento de **RFX\_** .  
  
## Información general sobre el intercambio de campos de registros  
 Todas las funciones de campo de conjunto de registros se hace con el código de C\+\+.  No hay recursos especiales o macros mágicas.  El núcleo del mecanismo es una función virtual que se debe invalidar en cada clase derivada de conjunto de registros.  Se encuentra siempre en este formulario:  
  
```  
void CMySet::DoFieldExchange(CFieldExchange* pFX)  
{  
  //{{AFX_FIELD_MAP(CMySet)  
  <recordset exchange field type call>  
  <recordset exchange function call>  
  //}}AFX_FIELD_MAP  
}  
```  
  
 Los comentarios especiales de AFX de formato permiten que ClassWizard busque y editar el código en esta función.  El código que no es compatible con ClassWizard debe colocarse fuera de los comentarios especiales de formato.  
  
 En el ejemplo anterior, \<el recordset\_exchange\_field\_type\_call\> está en el formulario:  
  
```  
pFX->SetFieldType(CFieldExchange::outputColumn);  
```  
  
 y \<el recordset\_exchange\_function\_call\> está en el formulario:  
  
```  
RFX_Custom(pFX, "Col2", m_Col2);  
```  
  
 La mayoría de las funciones de **RFX\_** tienen tres argumentos como se indicó anteriormente, pero algunos \(por ejemplo.  `RFX_Text` y `RFX_Binary`\) tienen argumentos opcionales adicionales.  
  
 Más de un **RFX\_** se puede incluir en cada función de `DoDataExchange` .  
  
 Vea “afxdb.h” para una lista de todas las rutinas de intercambio de campos de conjunto de registros proporcionadas MFC.  
  
 Las llamadas de campo de conjunto de registros son una manera de registrar las ubicaciones de memoria \(normalmente miembros de datos\) para almacenar los datos de campo para una clase de **CMySet** .  
  
## Notas  
 Las funciones de campo de conjunto de registros están diseñados para trabajar solo con las clases de `CRecordset` .  No suelen usarse por otras clases MFC.  
  
 Los valores iniciales de datos se establecen en el constructor estándar de C\+\+, normalmente en un bloque con `//{{AFX_FIELD_INIT(CMylSet)` y comentarios de `//}}AFX_FIELD_INIT` .  
  
 Cada función de **RFX\_** debe admitir varias operaciones, extendiéndose de devolver el estado modificado de campo a almacenar el campo con objeto de modificar el campo.  
  
 Cada función que llama a `DoFieldExchange` \(por ejemplo `SetFieldNull`, `IsFieldDirty`\), realiza su propia inicialización alrededor de la llamada a `DoFieldExchange`.  
  
## ¿Cómo funciona?  
 No necesita comprender lo siguiente para utilizar el intercambio de campos.  Sin embargo, entender el funcionamiento de ésta en segundo plano le ayudará a escribir el propio procedimiento de intercambio.  
  
 La función miembro de `DoFieldExchange` es como la función miembro de `Serialize` — es responsable de obtener o establecer datos a y desde un formulario externo \(en este caso columnas de resultados de una consulta de ODBC\) from\/to datos de miembros en la clase.  El parámetro de `pFX` es el contexto para hacer de intercambio y es similar al parámetro de `CArchive` a `CObject::Serialize`.  `pFX` \(un objeto de `CFieldExchange` \) tiene un indicador de la operación, el cual es similar, sólo una generalización de indicador de la dirección de `CArchive` .  Una función RFX puede tener que admitir las operaciones siguientes:  
  
-   **BindParam** — Indicate donde ODBC debe recuperar los datos de parámetro  
  
-   **BindFieldToColumn** — Indicate donde ODBC debe recuperar o los datos de outputColumn de depósito  
  
-   **Fixup** — longitudes concretas de **CString\/CByteArray** , establezca el bit de estado NULL  
  
-   **MarkForAddNew** — marca modificada si el valor ha cambiado desde llamada a AddNew  
  
-   **MarkForUpdate** — marca modificada si el valor ha cambiado desde llamada de edición  
  
-   **Name** — Agregue los nombres de campo para los campos marcó modificado  
  
-   **NameValue** — anexe “\<name\=\>de columna?” para modificado como campos  
  
-   **Valor** — Anexe “?” seguido de separador, como “,” o ''  
  
-   `SetFieldDirty` — \(es decir cambiado\) campo modificado mordido estado determinado  
  
-   `SetFieldNull` — estado determinado mordido indicando el valor NULL para el campo  
  
-   `IsFieldDirty` — valor devuelto de bits modificado de estado  
  
-   `IsFieldNull` — valor devuelto de bits null de estado  
  
-   `IsFieldNullable` — TRUE return si el campo puede contener valores nulos  
  
-   **StoreField** \(valor de campo del archivo  
  
-   **LoadField** \(valor de campo almacenado recarga  
  
-   **GetFieldInfoValue** — información general return en un campo  
  
-   **GetFieldInfoOrdinal** — información general return en un campo  
  
## Extensiones de usuario  
 Hay varias maneras de extender el mecanismo predeterminado RFX.  Se puede  
  
-   Agregue nuevos tipos de datos.  Por ejemplo:  
  
    ```  
    CBookmark  
    ```  
  
-   Agregue nuevos procedimientos de intercambio \(RFX\_???\).  
  
    ```  
    void AFXAPI RFX_Bigint(CFieldExchange* pFX, const char *szName,  
        BIGINT& value);  
    ```  
  
-   Tiene las llamadas de inclusión adicionales RFX de funciones miembro de `DoFieldExchange` condicional o cualquier otra instrucción válida de C\+\+.  
  
    ```  
    while (posExtraFields != NULL)  
    {  
        RFX_Text(pFX, m_listName.GetNext(posExtraFields),   
            m_listValue.GetNext(posExtraValues));  
    }  
    ```  
  
> [!NOTE]
>  Este código no se puede editar por ClassWizard y solo se debería usar fuera de los comentarios especiales de formato.  
  
## Escribir una personalizada RFX  
 Para escribir dispone de la función personalizados de RFX, se sugiere que copia una función existente RFX y modificarlo a dispone propósitos.  La selección de la derecha RFX de copiar puede crear el trabajo mucho más fácil.  Las funciones de algún RFX tienen algunas propiedades únicas que debe tener en cuenta al decidir cuál para copiar.  
  
 **RFX\_Long and RFX\_Int**:  
 Estas son las funciones más simples de RFX.  El valor de los datos no necesita ninguna interpretación especial, y se corrige el tamaño de datos.  
  
 **RFX\_Single and RFX\_Double**:  
 Como RFX\_Long y RFX\_Int anterior, estas funciones son simples y pueden utilizar la implementación predeterminada ampliamente.  Se almacenan en dbflt.cpp en lugar de dbrfx.cpp, sin embargo, para habilitar cargar la biblioteca de punto flotante en tiempo de ejecución si son explícitamente referencia.  
  
 **RFX\_Text and RFX\_Binary**:  
 Estas dos funciones reserva un buffer estático para contener la cadena\/información binaria, y deben registrar estos búferes con ODBC SQLBindCol en lugar de registrar &valor.  Debido a esto, estas dos funciones tienen partes de código de especial\- caso.  
  
 `RFX_Date`:  
 ODBC devuelve información de fecha y hora en su propia estructura de datos de TIMESTAMP\_STRUCT.  Esta función asigna dinámicamente un TIMESTAMP\_STRUCT como “proxy” para enviar y recibir datos de fecha y hora.  Varias operaciones deben transferir información de fecha y hora entre el objeto C\+\+ `CTime` y el proxy de TIMESTAMP\_STRUCT.  Esto complica esta función considerablemente, pero es un buen ejemplo de cómo utilizar un proxy para la transferencia de datos.  
  
 `RFX_LongBinary`:  
 Esta es la única función de biblioteca de clases RFX que no utiliza el enlace de columna para recibir y enviar datos.  Esta función omite la operación de BindFieldToColumn y en su lugar, durante la operación de la corrección, asigna almacenamiento para contener los datos de entrada de SQL\_LONGVARCHAR o de SQL\_LONGVARBINARY, realice una llamada a SQLGetData para recuperar el valor en el almacenamiento asignado.  Al prepararse para exponer valores de los datos al origen de datos \(como operaciones de NameValue y valor\), esta función usa la funcionalidad de DATA\_AT\_EXEC de ODBC.  Vea [Nota técnica 45](../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md) para obtener más información sobre cómo trabajar con SQL\_LONGVARBINARY y SQL\_LONGVARCHARs.  
  
 Al escribir poseer la función de **RFX\_** , podrá a menudo utilizar **CFieldExchange::Default** para implementar una operación determinada.  Busque la implementación predeterminado para la operación en cuestión.  Si realiza la operación se estaría escribiendo en la función de **RFX\_** que puede delegar a **CFieldExchange::Default.** Puede ver ejemplos de llamar a **CFieldExchange::Default** en dbrfx.cpp  
  
 Es importante llamar a `IsFieldType` al principio de la función RFX, y devuelve un valor inmediatamente si devuelve FALSE.  Este mecanismo conserva operaciones de parámetro de realizar en **outputColumns**, y viceversa \(como llamar a **BindParam** en **outputColumn**\).  Además, `IsFieldType` automáticamente el seguimiento del número de **outputColumns** \(`m_nFields`\) y params \(`m_nParams`\).  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)