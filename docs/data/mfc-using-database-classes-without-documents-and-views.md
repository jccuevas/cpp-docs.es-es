---
title: 'MFC: Utilizar clases de base de datos sin documentos ni vistas | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ba2e59b53524975f87e4ad7ffe99b9a4a3cc870d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093901"
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC: Utilizar clases de base de datos sin documentos ni vistas
A veces, no puede usar la arquitectura de documento/vista del marco de trabajo en las aplicaciones de base de datos. En este tema se explica:  
  
-   [Cuando no necesite usar documentos](#_core_when_you_don.92.t_need_documents) como la serialización de documentos.  
  
-   [Opciones del Asistente para aplicaciones](#_core_appwizard_options_for_documents_and_views) para admitir aplicaciones sin serialización y sin relacionadas con el documento **archivo** comandos de menú como **New**, **abiertos** , **Guardar**, y **Guardar como**.  
  
-   [Cómo trabajar con una aplicación que utiliza un documento mínimo](#_core_applications_with_minimal_documents).  
  
-   [Cómo estructurar una aplicación sin documentos ni vistas](#_core_applications_with_no_document).  
  
##  <a name="_core_when_you_don.92.t_need_documents"></a> Cuando no necesite documentos  
 Algunas aplicaciones tienen un concepto distinto de un documento. Estas aplicaciones suelen cargar todos o la mayoría de un archivo de almacenamiento en la memoria con un **abrir archivo** comando. Reescribir el archivo actualizado en el almacenamiento a la vez con un **Guardar archivo** o **Guardar como** comando. Lo que el usuario ve es un archivo de datos.  
  
 Sin embargo, algunas categorías de aplicaciones, no requieren un documento. Las aplicaciones de base de datos funcionan en cuanto a las transacciones. La aplicación selecciona los registros de una base de datos y las presenta al usuario, a menudo uno en uno. Lo que el usuario ve suele ser un único registro actual, que podría ser la única persona en la memoria.  
  
 Si la aplicación no requiere un documento para almacenar los datos, se puede omitir algunos o todos de arquitectura de documento/vista del marco de trabajo. ¿Cuánto Prescinda de ella dependerá el enfoque que prefiera. Es posible que:  
  
-   Usar un documento mínimo como un lugar para almacenar una conexión al origen de datos pero dispensar con características de documento normal, como la serialización. Esto es útil cuando desea tener varias vistas de los datos y desea sincronizar todas las vistas, actualizarlos todos a la vez y así sucesivamente.  
  
-   Utilice una ventana de marco, en la que dibujar directamente, en lugar de usar una vista. En este caso, se omite el documento y almacenan los datos o conexiones de datos en el objeto de ventana de marco.  
  
##  <a name="_core_appwizard_options_for_documents_and_views"></a> Opciones del Asistente para aplicaciones de documentos y vistas  
 El Asistente para aplicaciones MFC tiene varias opciones **selecciona la compatibilidad con la base de datos**, que se muestran en la tabla siguiente. Si utiliza al Asistente para aplicaciones MFC para crear una aplicación, todas estas opciones producen aplicaciones con documentos y vistas. Algunas opciones proporcionan documentos y vistas que omiten la funcionalidad de los documentos. Para obtener más información, consulte [compatibilidad de base de datos, Asistente para aplicaciones MFC](../mfc/reference/database-support-mfc-application-wizard.md).  
  
|Opción|Ver|Documento|  
|------------|----------|--------------|  
|**Ninguno**|Se deriva de `CView`.|No proporciona ninguna compatibilidad de base de datos. Ésta es la opción predeterminada.<br /><br /> Si selecciona el **compatibilidad con la arquitectura documento/vista** opción el [tipo de aplicación, Asistente para aplicaciones MFC](../mfc/reference/application-type-mfc-application-wizard.md) página, obtendrá compatibilidad total con documentos incluidos serialización y `New`,  **Abra**, **guardar**, y **Guardar como** comandos en el **archivo** menú. Vea [aplicaciones sin documentos](#_core_applications_with_no_document).|  
|**Sólo los archivos de encabezado**|Se deriva de `CView`.|Proporciona el nivel básico de compatibilidad de base de datos para la aplicación.<br /><br /> Incluye Afxdb.h. Agrega bibliotecas de vínculos, pero no crea las clases específicas de la base de datos. También puede crear conjuntos de registros más tarde y usarlos para examinar y actualizar registros.|  
|**Vista de base de datos sin compatibilidad con archivos**|Deriva de `CRecordView`|Proporciona compatibilidad con documentos pero no hay compatibilidad con la serialización. Documento puede almacenar el conjunto de registros y coordinar varias vistas; no admite la serialización o la `New`, **abiertos**, **guardar**, y **Guardar como** comandos. Vea [aplicaciones con documentos mínimos](#_core_applications_with_minimal_documents). Si incluye una vista de base de datos, debe especificar el origen de los datos.<br /><br /> Incluye archivos de encabezado de la base de datos, bibliotecas de vínculos, una vista de registros y un conjunto de registros. (Disponible únicamente para las aplicaciones con la **compatibilidad con la arquitectura documento/vista** opción seleccionada en el [tipo de aplicación, Asistente para aplicaciones MFC](../mfc/reference/application-type-mfc-application-wizard.md) página.)|  
|**Vista de base de datos con compatibilidad con archivos**|Deriva de `CRecordView`|Proporciona compatibilidad total con documentos, incluida la serialización y relacionadas con el documento **archivo** comandos de menú. Las aplicaciones de base de datos suelen funcionan en una base por registro en lugar de en un archivo por base de modo que no necesitan la serialización. Sin embargo, podría tener un uso especial para la serialización. Vea [aplicaciones con documentos mínimos](#_core_applications_with_minimal_documents). Si incluye una vista de base de datos, debe especificar el origen de los datos.<br /><br /> Incluye archivos de encabezado de la base de datos, bibliotecas de vínculos, una vista de registros y un conjunto de registros. (Disponible únicamente para las aplicaciones con la **compatibilidad con la arquitectura documento/vista** opción seleccionada en el [tipo de aplicación, Asistente para aplicaciones MFC](../mfc/reference/application-type-mfc-application-wizard.md) página.)|  
  
 Para obtener una explicación de las alternativas a la serialización y usos alternativos para la serialización, vea [serialización: serialización frente. Base de datos de entrada/salida](../mfc/serialization-serialization-vs-database-input-output.md).  
  
##  <a name="_core_applications_with_minimal_documents"></a> Aplicaciones con documentos mínimos  
 El Asistente para aplicaciones MFC tiene dos opciones que admiten aplicaciones de acceso a datos basado en formularios. Cada opción crea un `CRecordView`-deriva la clase de vista y un documento. Se diferencian en lo que dejan fuera del documento.  
  
###  <a name="_core_a_document_without_file_support"></a> Documento sin compatibilidad con archivos  
 Seleccione la opción de base de datos del Asistente para aplicaciones **vista sin compatibilidad con archivos de base de datos** si no necesita la serialización de documentos. El documento tiene los siguientes objetivos útiles:  
  
-   Es un lugar conveniente para almacenar un `CRecordset` objeto.  
  
     Conceptos de documento normal asemeja a este uso: el documento almacena los datos (o, en este caso, un conjunto de registros) y la vista es una vista del documento.  
  
-   Si la aplicación presenta varias vistas (por ejemplo, varias vistas de registros), un documento admite coordinar las vistas.  
  
     Si varias vistas muestran los mismos datos, puede usar el `CDocument::UpdateAllViews` función de miembro para coordinar las actualizaciones de todas las vistas cuando cualquier vista cambia los datos.  
  
 Normalmente se utiliza esta opción para las aplicaciones sencillas basadas en formularios. El Asistente para la aplicación es compatible con una estructura adecuada para dichas aplicaciones automáticamente.  
  
###  <a name="_core_a_document_with_file_support"></a> Documento con compatibilidad con archivos  
 Seleccione la opción de base de datos del Asistente para aplicaciones **vista con compatibilidad con archivos de base de datos** cuando tenga un uso alternativo para el objeto relacionado en el documento de **archivo** comandos de menú y serialización de documentos. Para la parte de acceso a datos del programa, puede usar el documento de la misma manera como se describe en [documento sin compatibilidad con archivos](#_core_a_document_without_file_support). Puede usar la funcionalidad de serialización del documento, por ejemplo, para leer y escribir un documento de perfil de usuario serializado que almacena las preferencias del usuario u otra información útil. Para obtener más ideas, vea [serialización: serialización frente. Base de datos de entrada/salida](../mfc/serialization-serialization-vs-database-input-output.md).  
  
 El Asistente para la aplicación es compatible con esta opción, pero debe escribir el código que serializa el documento. Almacene la información serializada en miembros de datos del documento.  
  
##  <a name="_core_applications_with_no_document"></a> Aplicaciones sin documentos  
 En ocasiones, puede escribir una aplicación que no utilice documentos ni vistas. Sin documentos, almacenar los datos (como un `CRecordset` objeto) en la clase de ventana de marco o la clase de aplicación. Los requisitos adicionales dependen de si la aplicación presenta una interfaz de usuario.  
  
###  <a name="_core_database_support_with_a_user_interface"></a> Compatibilidad de base de datos con una interfaz de usuario  
 Si tiene una interfaz de usuario (que no sea, por ejemplo, una interfaz de línea de comandos de consola), la aplicación dibuja directamente en el área de cliente de la ventana de marco en lugar de a una vista. Este tipo de aplicación no utiliza `CRecordView`, `CFormView`, o `CDialog` para su interfaz de usuario principal, pero suele usar `CDialog` para cuadros de diálogo normales.  
  
###  <a name="_core_writing_applications_without_documents"></a> Escribir aplicaciones sin documentos  
 Dado que el Asistente para aplicaciones no admite la creación de aplicaciones sin documentos, debe escribir su propio `CWinApp`-clase derivada y, si es necesario, cree también un `CFrameWnd` o `CMDIFrameWnd` clase. Invalidar `CWinApp::InitInstance` y declarar un objeto de aplicación como:  
  
```  
CYourNameApp theApp;  
```  
  
 El marco de trabajo proporciona el mecanismo de mapa de mensajes y muchas otras características.  
  
###  <a name="_core_database_support_separate_from_the_user_interface"></a> Independiente de compatibilidad de base de datos de la interfaz de usuario  
 Algunas aplicaciones necesitan ninguna interfaz de usuario o solo una mínima. Por ejemplo, suponga que está escribiendo:  
  
-   Un objeto de acceso a datos intermedio que llaman otras aplicaciones (clientes) para un procesamiento especial de datos entre la aplicación y el origen de datos.  
  
-   Una aplicación que procesa datos sin intervención del usuario, por ejemplo, una aplicación que mueve datos de un formato de base de datos a otro u otra que realiza cálculos y actualizaciones por lotes.  
  
 Debido a que no hay ningún documento posee la `CRecordset` objeto, probablemente desee almacenar como un miembro de datos incrustado en su `CWinApp`-deriva la clase de la aplicación. Las alternativas incluyen:  
  
-   No se debe mantener un permanente `CRecordset` objeto en absoluto. Puede pasar **NULL** a los constructores de clase de conjunto de registros. En ese caso, el marco de trabajo crea un archivo temporal `CDatabase` objeto según se indica en el conjunto de registros `GetDefaultConnect` función miembro. Éste es el enfoque alternativo más probable.  
  
-   Realizar la `CRecordset` una variable global del objeto. Esta variable debe ser un puntero a un objeto de conjunto de registros que se crea dinámicamente en su `CWinApp::InitInstance` invalidar. Esto evita el intento de construir el objeto antes de que se inicialice el marco de trabajo.  
  
-   Uso de objetos de conjunto de registros como lo haría en el contexto de un documento o una vista. Crear conjuntos de registros en el miembro de las funciones de la aplicación o los objetos de ventana de marco.  
  
## <a name="see-also"></a>Vea también  
 [Clases de bases de datos MFC](../data/mfc-database-classes-odbc-and-dao.md)