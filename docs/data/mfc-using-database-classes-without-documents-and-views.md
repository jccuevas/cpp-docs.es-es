---
title: 'MFC: Uso de clases de base de datos sin documentos ni vistas'
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
ms.openlocfilehash: ab9946609fa20c4644873a684a754cbc8a41742f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396020"
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC: Uso de clases de base de datos sin documentos ni vistas

A veces es posible que no desea utilizar la arquitectura documento/vista de .NET framework en las aplicaciones de base de datos. En este tema se explica:

- [Cuando no necesite usar documentos](#_core_when_you_don.92.t_need_documents) como la serialización de documentos.

- [Opciones de Asistente para la aplicación](#_core_appwizard_options_for_documents_and_views) para admitir aplicaciones sin serialización ni relacionadas con documentos **archivo** como comandos de menú **New**, **abierto** , **Guardar**, y **Guardar como**.

- [Cómo trabajar con una aplicación que utiliza un documento mínimo](#_core_applications_with_minimal_documents).

- [Cómo estructurar una aplicación sin documentos ni vistas](#_core_applications_with_no_document).

##  <a name="_core_when_you_don.92.t_need_documents"></a> Cuando no es necesario en documentos

Algunas aplicaciones tienen un concepto diferente de un documento. Estas aplicaciones suelen cargar todos o la mayoría de un archivo de almacenamiento en la memoria con un **abrir archivo** comando. Escriben el archivo actualizado de almacenamiento a la vez con un **Guardar archivo** o **Guardar como** comando. Lo que el usuario ve es un archivo de datos.

Sin embargo, algunas categorías de aplicaciones, no requieren un documento. Las aplicaciones de base de datos funcionan en cuanto a transacciones. La aplicación selecciona los registros de una base de datos y las presenta al usuario, a menudo una a la vez. Un único registro actual, que podría ser la única en la memoria es lo que el usuario ve.

Si la aplicación no requiere un documento para almacenar los datos, se puede omitir algunos o todos de la arquitectura de documento/vista de .NET framework. ¿Cuánto prescinden depende el enfoque que prefiera. Es posible que:

- Usar un documento mínimo como un lugar para almacenar una conexión al origen de datos y prescindir de las características de documento normal, como la serialización. Esto es útil cuando desea tener varias vistas de los datos y desea sincronizar todas las vistas, actualizarlos a la vez y así sucesivamente.

- Utilice una ventana de marco, en la que se dibuja directamente en lugar de usar una vista. En este caso, se omite el documento y almacenarían los datos o conexiones de datos en el objeto de ventana de marco.

##  <a name="_core_appwizard_options_for_documents_and_views"></a> Opciones de Asistente para la aplicación para documentos y vistas

El Asistente para aplicaciones MFC tiene varias opciones **seleccione soporte técnico de la base de datos**, que se enumeran en la tabla siguiente. Si usa al Asistente para aplicaciones MFC para crear una aplicación, todas estas opciones producen aplicaciones con documentos y vistas. Algunas opciones proporcionan documentos y vistas que omiten funcionalidad documentos innecesarios. Para obtener más información, consulte [soporte técnico de la base de datos, Asistente para aplicaciones MFC](../mfc/reference/database-support-mfc-application-wizard.md).

|Opción|Ver|Documento|
|------------|----------|--------------|
|**Ninguno**|Se deriva de `CView`.|No proporciona ninguna compatibilidad de base de datos. Ésta es la opción predeterminada.<br /><br /> Si selecciona el **compatibilidad con la arquitectura documento/vista** opción el [tipo de aplicación, Asistente para aplicaciones MFC](../mfc/reference/application-type-mfc-application-wizard.md) página, obtendrá compatibilidad con documentos completo incluida la serialización y **nuevo** , **Abierto**, **guardar**, y **Guardar como** comandos en el **archivo** menú. Consulte [aplicaciones sin documentos](#_core_applications_with_no_document).|
|**Archivos de encabezado**|Se deriva de `CView`.|Proporciona el nivel básico de compatibilidad de base de datos para la aplicación.<br /><br /> Incluye Afxdb.h. Agrega las bibliotecas de vínculos, pero no crea clases específicas de la base de datos. Puede crear conjuntos de registros más adelante y usarlos para examinar y actualizar registros.|
|**Vista de base de datos sin compatibilidad con archivos**|Deriva de `CRecordView`|Proporciona compatibilidad con documentos pero no con la serialización. Puede almacenar el conjunto de registros y coordinar varias vistas; documento no admite la serialización o la **New**, **abierto**, **guardar**, y **Guardar como** comandos. Consulte [aplicaciones con documentos mínimos](#_core_applications_with_minimal_documents). Si incluye una vista de base de datos, debe especificar el origen de datos.<br /><br /> Incluye un conjunto de registros, las bibliotecas de vínculos, una vista de registros y archivos de encabezado de la base de datos. (Disponible solo para las aplicaciones con el **compatibilidad con la arquitectura documento/vista** opción seleccionada en el [tipo de aplicación, Asistente para aplicaciones MFC](../mfc/reference/application-type-mfc-application-wizard.md) página.)|
|**Vista de base de datos con compatibilidad con archivos**|Deriva de `CRecordView`|Proporciona compatibilidad total con documentos, incluida la serialización y relacionadas con documentos **archivo** comandos de menú. Las aplicaciones de base de datos se suelen aplicar a una base por registro en lugar de en un archivo por lo que no necesitan la serialización. Sin embargo, podría tener un uso especial para la serialización. Consulte [aplicaciones con documentos mínimos](#_core_applications_with_minimal_documents). Si incluye una vista de base de datos, debe especificar el origen de datos.<br /><br /> Incluye un conjunto de registros, las bibliotecas de vínculos, una vista de registros y archivos de encabezado de la base de datos. (Disponible solo para las aplicaciones con el **compatibilidad con la arquitectura documento/vista** opción seleccionada en el [tipo de aplicación, Asistente para aplicaciones MFC](../mfc/reference/application-type-mfc-application-wizard.md) página.)|

Para obtener una explicación de las alternativas a la serialización y usos alternativos para la serialización, vea [serialización: serialización frente a Base de datos de entrada/salida](../mfc/serialization-serialization-vs-database-input-output.md).

##  <a name="_core_applications_with_minimal_documents"></a> Aplicaciones con documentos mínimos

El Asistente para aplicaciones MFC tiene dos opciones que admiten aplicaciones de acceso a datos basada en formularios. Cada opción crea un `CRecordView`-derivado de la clase de vista y un documento. Se diferencian en lo que dejan fuera del documento.

###  <a name="_core_a_document_without_file_support"></a> Documento sin compatibilidad con archivos

Seleccione la opción de base de datos del Asistente para aplicaciones **vista sin compatibilidad con archivos de base de datos** si no necesita la serialización de documentos. El documento tiene las siguientes finalidades útiles:

- Es un lugar conveniente para almacenar un `CRecordset` objeto.

   Este uso es semejante a los conceptos de documento normal: el documento almacena los datos (o, en este caso, un conjunto de registros) y la vista es una vista del documento.

- Si la aplicación presenta varias vistas (por ejemplo, varias vistas de registros), un documento admite la coordinación de las vistas.

   Si varias vistas muestran los mismos datos, puede usar el `CDocument::UpdateAllViews` función miembro para coordinar las actualizaciones a todas las vistas cuando cualquier vista cambia los datos.

Normalmente, use esta opción para las aplicaciones sencillas basadas en formularios. El Asistente para la aplicación es compatible con una estructura práctica para tales aplicaciones automáticamente.

###  <a name="_core_a_document_with_file_support"></a> Documento con compatibilidad con archivos

Seleccione la opción de base de datos del Asistente para aplicaciones **vista con compatibilidad con archivos de base de datos** cuando tenga un uso alternativo para el objeto relacionado en el documento **archivo** comandos de menú y serialización de documentos. Para la parte de acceso a datos del programa, puede usar el documento de la misma manera como se describe en [documento sin compatibilidad con archivos](#_core_a_document_without_file_support). Puede usar la funcionalidad de serialización del documento, por ejemplo, para leer y escribir un documento de perfil de usuario serializado que almacena las preferencias del usuario u otra información útil. Para obtener más ideas, consulte [serialización: serialización frente a Base de datos de entrada/salida](../mfc/serialization-serialization-vs-database-input-output.md).

El Asistente para la aplicación es compatible con esta opción, pero debe escribir el código que serializa el documento. Store la información serializada en miembros de datos del documento.

##  <a name="_core_applications_with_no_document"></a> Aplicaciones sin documentos

A veces es posible que desee escribir una aplicación que no utiliza documentos ni vistas. Sin documentos, almacena los datos (como un `CRecordset` objeto) en la clase de ventana de marco o la clase de aplicación. Los requisitos adicionales dependen de si la aplicación presenta una interfaz de usuario.

###  <a name="_core_database_support_with_a_user_interface"></a> Compatibilidad con la base de datos con una interfaz de usuario

Si tiene una interfaz de usuario (que no sea, por ejemplo, una interfaz de línea de comandos de consola), la aplicación dibuja directamente en el área de cliente de la ventana de marco en lugar de en una vista. Este tipo de aplicación no utiliza `CRecordView`, `CFormView`, o `CDialog` para su interfaz de usuario principal, pero normalmente se usa `CDialog` para cuadros de diálogo normales.

###  <a name="_core_writing_applications_without_documents"></a> Escritura de aplicaciones sin documentos

Dado que el Asistente para la aplicación no admite la creación de aplicaciones sin documentos, debe escribir su propio `CWinApp`-clase derivada y, si es necesario, cree también un `CFrameWnd` o `CMDIFrameWnd` clase. Invalidar `CWinApp::InitInstance` y declarar un objeto de aplicación como:

```cpp
CYourNameApp theApp;
```

El marco de trabajo proporciona el mecanismo de mapa de mensajes y muchas otras características.

###  <a name="_core_database_support_separate_from_the_user_interface"></a> Independiente de compatibilidad de base de datos desde la interfaz de usuario

Algunas aplicaciones necesitan ninguna interfaz de usuario o solo una mínima. Por ejemplo, supongamos que está escribiendo:

- Un objeto de acceso a datos intermedio que llaman otras aplicaciones (clientes) para un procesamiento especial de datos entre la aplicación y el origen de datos.

- Una aplicación que procesa datos sin intervención del usuario, como una aplicación que mueve los datos de un formato de base de datos a otro u otra que realiza cálculos y actualizaciones por lotes.

Porque no hay ningún documento posee el `CRecordset` objeto, que probablemente quiera almacenarla como un miembro de datos incrustados en su `CWinApp`-derivado de la clase de aplicación. Las alternativas incluyen:

- No mantener una permanentes `CRecordset` objeto en absoluto. Puede pasar NULL para los constructores de clases de conjunto de registros. En ese caso, el marco de trabajo crea un archivo temporal `CDatabase` objeto utilizando la información en el conjunto de registros `GetDefaultConnect` función miembro. Este es el enfoque alternativo más probable.

- Realizar la `CRecordset` una variable global de objeto. Esta variable debe ser un puntero a un objeto de conjunto de registros que se crea dinámicamente en su `CWinApp::InitInstance` invalidar. Esto evita el intento de construir el objeto antes de que se inicializa el marco de trabajo.

- Uso de objetos de conjunto de registros como lo haría en el contexto de un documento o una vista. Crear conjuntos de registros en el miembro de las funciones de la aplicación o los objetos de ventana de marco.

## <a name="see-also"></a>Vea también

[Clases de bases de datos MFC](../data/mfc-database-classes-odbc-and-dao.md)