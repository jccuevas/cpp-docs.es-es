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
ms.openlocfilehash: 57a7abd89bc9bfb465912a35c21f9780668f4466
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213361"
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC: Utilizar clases de base de datos sin documentos ni vistas

En ocasiones, es posible que no desee usar la arquitectura documento/vista del marco de trabajo en las aplicaciones de base de datos. En este tema se explica:

- [Cuando no es necesario usar documentos](#_core_when_you_don.92.t_need_documents) como la serialización de documentos.

- [Opciones del Asistente para aplicaciones](#_core_appwizard_options_for_documents_and_views) para admitir aplicaciones sin serialización y sin comandos de menú **archivo** relacionados con documentos como **nuevo**, **abrir**, **Guardar**y **Guardar como**.

- [Cómo trabajar con una aplicación que usa un documento mínimo](#_core_applications_with_minimal_documents).

- [Cómo estructurar una aplicación sin ningún documento ni vista](#_core_applications_with_no_document).

##  <a name="when-you-do-not-need-documents"></a><a name="_core_when_you_don.92.t_need_documents"></a>Si no necesita documentos

Algunas aplicaciones tienen un concepto distinto de un documento. Normalmente, estas aplicaciones cargan o la mayoría de un archivo desde el almacenamiento en la memoria con un comando de **archivo abierto** . Escriben el archivo actualizado en el almacenamiento todos a la vez con un comando **Guardar archivo** o **Guardar como** . Lo que ve el usuario es un archivo de datos.

Sin embargo, algunas categorías de aplicaciones no requieren un documento. Las aplicaciones de base de datos funcionan en términos de transacciones. La aplicación selecciona registros de una base de datos y los presenta al usuario, a menudo de uno en uno. Lo que ve el usuario suele ser un solo registro actual, que puede ser el único en la memoria.

Si su aplicación no requiere un documento para almacenar los datos, puede dispensar de la arquitectura de documento/vista del marco de trabajo. El grado de dispensado dependerá del enfoque que prefiera. Puede:

- Use un documento mínimo como un lugar para almacenar una conexión con el origen de datos, pero dispensado por las características de documento normales, como la serialización. Esto resulta útil si desea varias vistas de los datos y desea sincronizar todas las vistas, actualizándolos todas a la vez, etc.

- Use una ventana de marco en la que dibuje directamente, en lugar de usar una vista. En este caso, se omite el documento y se almacenan los datos o las conexiones de datos en el objeto de ventana de marco.

##  <a name="application-wizard-options-for-documents-and-views"></a><a name="_core_appwizard_options_for_documents_and_views"></a>Opciones del Asistente para aplicaciones para documentos y vistas

El Asistente para aplicaciones MFC tiene varias opciones en **seleccionar compatibilidad con bases de datos**, que se enumeran en la tabla siguiente. Si usa el Asistente para aplicaciones MFC para crear una aplicación, todas estas opciones generan aplicaciones con documentos y vistas. Algunas opciones proporcionan documentos y vistas que omiten la funcionalidad innecesaria del documento. Para obtener más información, vea [compatibilidad con bases de datos, Asistente para aplicaciones MFC](../mfc/reference/database-support-mfc-application-wizard.md).

|Opción|Ver|Documento|
|------------|----------|--------------|
|**None**|Se deriva de `CView`.|No proporciona compatibilidad con bases de datos. Ésta es la opción predeterminada.<br /><br /> Si selecciona la opción **compatibilidad con la arquitectura de documento/vista** en la página [tipo de aplicación, Asistente para aplicaciones MFC](../mfc/reference/application-type-mfc-application-wizard.md) , obtendrá compatibilidad total con documentos, incluidos los comandos **nuevo**, **abrir**, **Guardar**y **Guardar como** en el menú **archivo** . Vea [aplicaciones sin documento](#_core_applications_with_no_document).|
|**Solo archivos de encabezado**|Se deriva de `CView`.|Proporciona el nivel básico de compatibilidad con bases de datos para la aplicación.<br /><br /> Incluye Afxdb. h. Agrega bibliotecas de vínculos, pero no crea ninguna clase específica de base de datos. Puede crear conjuntos de registros más adelante y usarlos para examinar y actualizar registros.|
|**Vista de base de datos sin compatibilidad con archivos**|Derivado de `CRecordView`|Proporciona compatibilidad con documentos pero no admite la serialización. El documento puede almacenar un conjunto de registros y coordinar varias vistas; no admite la serialización ni los comandos **nuevos**, **abrir**, **Guardar**y **Guardar como** . Vea [aplicaciones con documentos mínimos](#_core_applications_with_minimal_documents). Si incluye una vista de base de datos, debe especificar el origen de los datos.<br /><br /> Incluye archivos de encabezado de base de datos, bibliotecas de vínculos, una vista de registros y un conjunto de registros. (Disponible solo para aplicaciones con la opción de **compatibilidad con la arquitectura documento/vista** seleccionada en la página [tipo de aplicación, Asistente para aplicaciones MFC](../mfc/reference/application-type-mfc-application-wizard.md) ).|
|**Vista de base de datos con compatibilidad con archivos**|Derivado de `CRecordView`|Proporciona compatibilidad completa con documentos, incluidos los comandos de menú de **archivos** relacionados con la serialización y los documentos. Las aplicaciones de base de datos normalmente operan por registro en lugar de por archivo, por lo que no necesitan serialización. Sin embargo, podría tener un uso especial para la serialización. Vea [aplicaciones con documentos mínimos](#_core_applications_with_minimal_documents). Si incluye una vista de base de datos, debe especificar el origen de los datos.<br /><br /> Incluye archivos de encabezado de base de datos, bibliotecas de vínculos, una vista de registros y un conjunto de registros. (Disponible solo para aplicaciones con la opción de **compatibilidad con la arquitectura documento/vista** seleccionada en la página [tipo de aplicación, Asistente para aplicaciones MFC](../mfc/reference/application-type-mfc-application-wizard.md) ).|

Para obtener una explicación de las alternativas a la serialización y los usos alternativos para la serialización, vea [serialización: serialización frente a entrada/salida de bases de datos](../mfc/serialization-serialization-vs-database-input-output.md).

##  <a name="applications-with-minimal-documents"></a><a name="_core_applications_with_minimal_documents"></a>Aplicaciones con documentos mínimos

El Asistente para aplicaciones MFC tiene dos opciones que admiten aplicaciones de acceso a datos basado en formularios. Cada opción crea una clase de vista derivada de `CRecordView`y un documento. Se diferencian en lo que dejan fuera del documento.

###  <a name="document-without-file-support"></a><a name="_core_a_document_without_file_support"></a>Documento sin compatibilidad con archivos

Seleccione la opción de base de datos vista de base de datos del Asistente para aplicaciones **sin compatibilidad con archivos** si no necesita la serialización de documentos. El documento sirve para los siguientes fines útiles:

- Es un lugar adecuado para almacenar un objeto de `CRecordset`.

   Este uso se asemeja a los conceptos de documentos normales: el documento almacena los datos (o, en este caso, un conjunto de registros) y la vista es una vista del documento.

- Si la aplicación presenta varias vistas (como varias vistas de registros), un documento admite la coordinación de las vistas.

   Si varias vistas muestran los mismos datos, puede usar la función miembro `CDocument::UpdateAllViews` para coordinar las actualizaciones de todas las vistas cuando cualquier vista cambie los datos.

Normalmente, esta opción se utiliza para las aplicaciones sencillas basadas en formularios. El Asistente para aplicaciones es compatible con una estructura adecuada para estas aplicaciones de forma automática.

###  <a name="document-with-file-support"></a><a name="_core_a_document_with_file_support"></a>Documento con compatibilidad con archivos

Seleccione la opción de base de datos vista de base de datos del Asistente para aplicaciones **con compatibilidad con archivos** cuando tenga un uso alternativo para los comandos del menú **archivo** relacionados con el documento y la serialización de documentos. Para la parte de acceso a datos del programa, puede utilizar el documento de la misma manera que se describe en el [documento sin compatibilidad con archivos](#_core_a_document_without_file_support). Puede utilizar la funcionalidad de serialización del documento, por ejemplo, para leer y escribir un documento de Perfil de usuario serializado que almacene las preferencias del usuario u otra información útil. Para obtener más ideas, vea [serialización: serialización frente a entrada/salida de bases de datos](../mfc/serialization-serialization-vs-database-input-output.md).

El Asistente para aplicaciones admite esta opción, pero debe escribir el código que serializa el documento. Almacene la información serializada en los miembros de datos del documento.

##  <a name="applications-with-no-document"></a><a name="_core_applications_with_no_document"></a>Aplicaciones sin documento

En ocasiones, es posible que desee escribir una aplicación que no use documentos ni vistas. Sin documentos, se almacenan los datos (por ejemplo, un objeto `CRecordset`) en la clase de ventana de marco o en la clase de aplicación. Cualquier requisito adicional depende de si la aplicación presenta una interfaz de usuario.

###  <a name="database-support-with-a-user-interface"></a><a name="_core_database_support_with_a_user_interface"></a>Compatibilidad con bases de datos con una interfaz de usuario

Si tiene una interfaz de usuario (distinta de, por ejemplo, una interfaz de línea de comandos de la consola), la aplicación dibuja directamente en el área de cliente de la ventana de marco en lugar de hacerlo en una vista. Este tipo de aplicación no usa `CRecordView`, `CFormView`o `CDialog` para su interfaz de usuario principal, pero normalmente usa `CDialog` para cuadros de diálogo normales.

###  <a name="writing-applications-without-documents"></a><a name="_core_writing_applications_without_documents"></a>Escribir aplicaciones sin documentos

Dado que el Asistente para aplicaciones no admite la creación de aplicaciones sin documentos, debe escribir su propia clase derivada de `CWinApp`y, si es necesario, crear también una clase `CFrameWnd` o `CMDIFrameWnd`. Invalide `CWinApp::InitInstance` y declare un objeto de aplicación como:

```cpp
CYourNameApp theApp;
```

El marco de trabajo sigue suministrando el mecanismo de mapa de mensajes y muchas otras características.

###  <a name="database-support-separate-from-the-user-interface"></a><a name="_core_database_support_separate_from_the_user_interface"></a>Compatibilidad con bases de datos independientes de la interfaz de usuario

Algunas aplicaciones no necesitan una interfaz de usuario o solo una mínima. Por ejemplo, supongamos que está escribiendo:

- Objeto de acceso a datos intermedio al que otras aplicaciones (clientes) llaman para el procesamiento especial de datos entre la aplicación y el origen de datos.

- Aplicación que procesa datos sin intervención del usuario, como una aplicación que mueve datos de un formato de base de datos a otro o uno que realiza cálculos y realiza actualizaciones por lotes.

Dado que ningún documento posee el objeto `CRecordset`, es probable que desee almacenarlo como miembro de datos incrustado en la clase de aplicación derivada de `CWinApp`. De forma alternativa, puede hacer lo siguiente:

- No mantener un objeto de `CRecordset` permanente. Puede pasar NULL a los constructores de la clase de conjunto de registros. En ese caso, el marco de trabajo crea un objeto temporal `CDatabase` con la información de la función miembro `GetDefaultConnect` del conjunto de registros. Este es el enfoque alternativo más probable.

- Convertir el objeto de `CRecordset` en una variable global. Esta variable debe ser un puntero a un objeto de conjunto de registros que se crea dinámicamente en el `CWinApp::InitInstance` invalidación. Esto evita intentar construir el objeto antes de que se inicialice el marco.

- Usar objetos de conjunto de registros como lo haría en el contexto de un documento o una vista. Cree conjuntos de registros en las funciones miembro de los objetos de la aplicación o de la ventana de marco.

## <a name="see-also"></a>Consulte también

[Clases de bases de datos MFC](../data/mfc-database-classes-odbc-and-dao.md)
