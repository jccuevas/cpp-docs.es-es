---
title: 'MFC: Utilizar clases de base de datos sin documentos ni vistas'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC applications [C++], without views
- documents [C++], applications without
- ODBC applications [C++]
- document/view architecture [C++], in databases
- files [C++], MFC
- database classes [C++], MFC
- CRecordView class, using in database applications
- database applications [C++], without views
- database applications [C++], application wizard options
- application wizards [C++], creating database applications
- ODBC [C++], file support in database applications
- ODBC applications [C++], without documents
- database applications [C++], without documents
- user interface [C++], drawing information
ms.assetid: 15bf52d4-91cf-4b1d-8b37-87c3ae70123a
ms.openlocfilehash: c914a449b73e7da876d2e05b894c016b53881c3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360668"
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC: Utilizar clases de base de datos sin documentos ni vistas

A veces es posible que no desee usar la arquitectura de documento/vista del marco de trabajo en las aplicaciones de base de datos. En este tema se explica:

- [Cuando no es necesario utilizar documentos](#_core_when_you_don.92.t_need_documents) como la serialización de documentos.

- [Opciones](#_core_appwizard_options_for_documents_and_views) del asistente de aplicaciones para admitir aplicaciones sin serialización y sin comandos de menú **Archivo** relacionados con documentos como **Nuevo**, **Abrir**, **Guardar**y **Guardar como**.

- [Cómo trabajar con una aplicación que utiliza un documento mínimo.](#_core_applications_with_minimal_documents)

- [Cómo estructurar una aplicación sin documento o vista.](#_core_applications_with_no_document)

## <a name="when-you-do-not-need-documents"></a><a name="_core_when_you_don.92.t_need_documents"></a>Cuando no necesita documentos

Algunas aplicaciones tienen un concepto distinto de un documento. Estas aplicaciones normalmente cargan todo o la mayor parte de un archivo desde el almacenamiento en la memoria con un comando **Abrir archivo.** Escriben el archivo actualizado en el almacenamiento a la vez con un comando **Guardar** archivo o **Guardar como.** Lo que el usuario ve es un archivo de datos.

Algunas categorías de aplicaciones, sin embargo, no requieren un documento. Las aplicaciones de base de datos funcionan en términos de transacciones. La aplicación selecciona registros de una base de datos y los presenta al usuario, a menudo uno a la vez. Lo que el usuario ve suele ser un único registro actual, que podría ser el único en la memoria.

Si la aplicación no requiere un documento para almacenar datos, puede prescindir de parte o toda la arquitectura de documento/vista del marco de trabajo. La cantidad que prescinda depende del enfoque que prefiera. Usted podría:

- Utilice un documento mínimo como lugar para almacenar una conexión con el origen de datos, pero prescinda de las características normales del documento, como la serialización. Esto es útil cuando desea varias vistas de los datos y desea sincronizar todas las vistas, actualizándolas todas a la vez y así sucesivamente.

- Utilice una ventana de marco, en la que dibuje directamente, en lugar de utilizar una vista. En este caso, se omite el documento y se almacenan las conexiones de datos o datos en el objeto de ventana de marco.

## <a name="application-wizard-options-for-documents-and-views"></a><a name="_core_appwizard_options_for_documents_and_views"></a>Opciones del Asistente para aplicaciones para documentos y vistas

El Asistente para aplicaciones MFC tiene varias opciones en **Seleccionar compatibilidad con bases**de datos , que se enumeran en la tabla siguiente. Si utiliza el Asistente para aplicaciones MFC para crear una aplicación, todas estas opciones generan aplicaciones con documentos y vistas. Algunas opciones proporcionan documentos y vistas que omiten la funcionalidad de documentos innecesaria. Para obtener más información, vea [Compatibilidad con bases de datos, Asistente para aplicaciones MFC](../mfc/reference/database-support-mfc-application-wizard.md).

|Opción|Ver|Documento|
|------------|----------|--------------|
|**None**|Se deriva de `CView`.|No proporciona compatibilidad con bases de datos. Ésta es la opción predeterminada.<br /><br /> Si selecciona la opción Compatibilidad con **arquitectura de documento/vista** en la página Tipo de [aplicación, Asistente para](../mfc/reference/application-type-mfc-application-wizard.md) aplicaciones MFC, obtendrá compatibilidad completa con documentos, incluidos los comandos Nueva y **Nuevo**, **Abrir**, **Guardar**y **Guardar** como en el menú **Archivo.** Consulte [Aplicaciones sin documento](#_core_applications_with_no_document).|
|**Sólo archivos de encabezado**|Se deriva de `CView`.|Proporciona el nivel básico de compatibilidad con la base de datos para la aplicación.<br /><br /> Incluye Afxdb.h. Agrega bibliotecas de vínculos, pero no crea ninguna clase específica de la base de datos. Puede crear conjuntos de registros más adelante y usarlos para examinar y actualizar registros.|
|**Vista de base de datos sin soporte de archivos**|Derivado de`CRecordView`|Proporciona compatibilidad con documentos, pero no compatibilidad con serialización. El documento puede almacenar conjuntos de registros y coordinar varias vistas; no admite la serialización ni los comandos **Nuevo**, **Abrir**, **Guardar**y **Guardar como.** Consulte [Aplicaciones con documentos mínimos](#_core_applications_with_minimal_documents). Si incluye una vista de base de datos, debe especificar el origen de los datos.<br /><br /> Incluye archivos de encabezado de base de datos, bibliotecas de vínculos, una vista de registros y un conjunto de registros. (Disponible solo para aplicaciones con la opción de compatibilidad con **arquitectura de documento/vista** seleccionada en la página Tipo de [aplicación, Asistente para aplicaciones MFC.)](../mfc/reference/application-type-mfc-application-wizard.md)|
|**Vista de base de datos con soporte de archivos**|Derivado de`CRecordView`|Proporciona compatibilidad completa con documentos, incluida la serialización y los comandos de menú **Archivo** relacionados con documentos. Las aplicaciones de base de datos suelen funcionar por registro en lugar de por archivo, por lo que no necesitan serialización. Sin embargo, es posible que tenga un uso especial para la serialización. Consulte [Aplicaciones con documentos mínimos](#_core_applications_with_minimal_documents). Si incluye una vista de base de datos, debe especificar el origen de los datos.<br /><br /> Incluye archivos de encabezado de base de datos, bibliotecas de vínculos, una vista de registros y un conjunto de registros. (Disponible solo para aplicaciones con la opción de compatibilidad con **arquitectura de documento/vista** seleccionada en la página Tipo de [aplicación, Asistente para aplicaciones MFC.)](../mfc/reference/application-type-mfc-application-wizard.md)|

Para obtener una explicación de las alternativas a la serialización y los usos alternativos para la serialización, vea [Serialización: serialización frente a entrada/salida](../mfc/serialization-serialization-vs-database-input-output.md)de base de datos .

## <a name="applications-with-minimal-documents"></a><a name="_core_applications_with_minimal_documents"></a>Aplicaciones con documentos mínimos

El Asistente para aplicaciones MFC tiene dos opciones que admiten aplicaciones de acceso a datos basadas en formularios. Cada opción `CRecordView`crea una clase de vista derivada y un documento. Se diferencian en lo que dejan fuera del documento.

### <a name="document-without-file-support"></a><a name="_core_a_document_without_file_support"></a>Documento sin soporte de archivos

Seleccione la opción de base de datos del asistente de aplicación Vista de base de datos **sin compatibilidad con archivos** si no necesita serialización de documentos. El documento sirve para los siguientes propósitos útiles:

- Es un lugar conveniente `CRecordset` para almacenar un objeto.

   Este uso es paralelo a los conceptos de documento ordinarios: el documento almacena los datos (o, en este caso, un conjunto de registros) y la vista es una vista del documento.

- Si la aplicación presenta varias vistas (por ejemplo, varias vistas de registros), un documento admite la coordinación de las vistas.

   Si varias vistas muestran los mismos datos, puede usar la `CDocument::UpdateAllViews` función miembro para coordinar las actualizaciones de todas las vistas cuando cualquier vista cambie los datos.

Normalmente se utiliza esta opción para aplicaciones sencillas basadas en formularios. El asistente de aplicaciones admite una estructura conveniente para este tipo de aplicaciones automáticamente.

### <a name="document-with-file-support"></a><a name="_core_a_document_with_file_support"></a>Documento con soporte de archivos

Seleccione la opción de base de datos del asistente de aplicación Vista de base de datos **con compatibilidad con archivos** cuando tenga un uso alternativo para los comandos de menú **Archivo** relacionados con documentos y la serialización de documentos. Para la parte de acceso a datos del programa, puede utilizar el documento de la misma manera que se describe en [Documento sin soporte](#_core_a_document_without_file_support)de archivos . Puede utilizar la capacidad de serialización del documento, por ejemplo, para leer y escribir un documento de perfil de usuario serializado que almacene las preferencias del usuario u otra información útil. Para obtener más ideas, consulte [Serialización: serialización frente a entrada/salida](../mfc/serialization-serialization-vs-database-input-output.md)de base de datos .

El asistente de aplicación admite esta opción, pero debe escribir el código que serializa el documento. Almacene la información serializada en los miembros de datos de documento.

## <a name="applications-with-no-document"></a><a name="_core_applications_with_no_document"></a>Aplicaciones sin documento

A veces es posible que desee escribir una aplicación que no utilice documentos o vistas. Sin documentos, almacene los `CRecordset` datos (como un objeto) en la clase de ventana de marco o en la clase de aplicación. Cualquier requisito adicional depende de si la aplicación presenta una interfaz de usuario.

### <a name="database-support-with-a-user-interface"></a><a name="_core_database_support_with_a_user_interface"></a>Soporte de base de datos con una interfaz de usuario

Si tiene una interfaz de usuario (que no sea, por ejemplo, una interfaz de línea de comandos de consola), la aplicación se dibuja directamente en el área de cliente de la ventana de marco en lugar de en una vista. Tal aplicación no `CRecordView`utiliza `CFormView`, `CDialog` , o para su interfaz de usuario principal, pero normalmente se utiliza `CDialog` para los cuadros de diálogo ordinarios.

### <a name="writing-applications-without-documents"></a><a name="_core_writing_applications_without_documents"></a>Escribir aplicaciones sin documentos

Dado que el asistente de aplicaciones no admite la `CWinApp`creación de aplicaciones sin documentos, debe escribir su propia clase derivada y, si es necesario, también crear una `CFrameWnd` clase o `CMDIFrameWnd` una clase. Invalide `CWinApp::InitInstance` y declare un objeto de aplicación como:

```cpp
CYourNameApp theApp;
```

El marco de trabajo todavía proporciona el mecanismo de mapa de mensajes y muchas otras características.

### <a name="database-support-separate-from-the-user-interface"></a><a name="_core_database_support_separate_from_the_user_interface"></a>Soporte de base de datos separado de la interfaz de usuario

Algunas aplicaciones no necesitan interfaz de usuario o solo una mínima. Por ejemplo, supongamos que está escribiendo:

- Objeto de acceso a datos intermedio que otras aplicaciones (clientes) llaman para un procesamiento especial de datos entre la aplicación y el origen de datos.

- Una aplicación que procesa datos sin intervención del usuario, como una aplicación que mueve datos de un formato de base de datos a otro o uno que realiza cálculos y realiza actualizaciones por lotes.

Dado que ningún `CRecordset` documento es propietario del objeto, es probable que `CWinApp`desee almacenarlo como un miembro de datos incrustado en la clase de aplicación derivada. Las alternativas incluyen:

- No mantener `CRecordset` un objeto permanente en absoluto. Puede pasar NULL a los constructores de clase de conjunto de registros. En ese caso, el `CDatabase` marco de trabajo crea un `GetDefaultConnect` objeto temporal mediante la información de la función miembro del conjunto de registros. Este es el enfoque alternativo más probable.

- Convertir `CRecordset` el objeto en una variable global. Esta variable debe ser un puntero a un objeto `CWinApp::InitInstance` de conjunto de registros que se crea dinámicamente en la invalidación. Esto evita intentar construir el objeto antes de inicializar el marco de trabajo.

- Usar objetos de conjunto de registros como lo haría en el contexto de un documento o una vista. Crear conjuntos de registros en las funciones miembro de la aplicación o objetos de ventana de marco.

## <a name="see-also"></a>Consulte también

[Clases de bases de datos MFC](../data/mfc-database-classes-odbc-and-dao.md)
