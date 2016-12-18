---
title: "MFC: Utilizar clases de base de datos sin documentos ni vistas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "asistentes para aplicaciones [C++], crear aplicaciones de bases de datos"
  - "CDaoRecordView (clase), utilizar en aplicaciones de bases de datos"
  - "CRecordView (clase), utilizar en aplicaciones de bases de datos"
  - "DAO [C++], compatibilidad de archivos en aplicaciones de bases de datos"
  - "DAO [C++], escribir aplicaciones"
  - "aplicaciones de base de datos [C++], opciones del asistente para aplicaciones"
  - "aplicaciones de base de datos [C++], sin documentos"
  - "aplicaciones de base de datos [C++], sin vistas"
  - "clases de base de datos [C++], MFC"
  - "arquitectura documento/vista [C++], en bases de datos"
  - "documentos [C++], aplicaciones sin"
  - "archivos [C++], MFC"
  - "ODBC [C++], compatibilidad de archivos en aplicaciones de bases de datos"
  - "aplicaciones ODBC [C++]"
  - "aplicaciones ODBC [C++], sin documentos"
  - "aplicaciones ODBC [C++], sin vistas"
  - "interfaz de usuario [C++], dibujar información"
ms.assetid: 15bf52d4-91cf-4b1d-8b37-87c3ae70123a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC: Utilizar clases de base de datos sin documentos ni vistas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En ocasiones no se tiene interés en utilizar la arquitectura documento\/vista del marco de trabajo en las aplicaciones de base de datos.  En este tema se explica:  
  
-   [Cuándo no debe utilizar documentos](#_core_when_you_don.92.t_need_documents); por ejemplo, en la serialización de documentos.  
  
-   [Opciones del Asistente para aplicaciones](#_core_appwizard_options_for_documents_and_views), que admiten aplicaciones sin serialización y sin comandos del menú **Archivo** relacionados con los documentos, como **Nuevo**, **Abrir**, **Guardar** y **Guardar como**.  
  
-   [Cómo trabajar con una aplicación que utiliza un documento mínimo](#_core_applications_with_minimal_documents).  
  
-   [Cómo estructurar una aplicación sin documentos ni vistas](#_core_applications_with_no_document).  
  
##  <a name="_core_when_you_don.92.t_need_documents"></a> Cuándo no debe utilizar documentos  
 Algunas aplicaciones utilizan un concepto distinto de lo que es un documento.  Estas aplicaciones suelen cargar la mayoría o la totalidad de un archivo desde el medio de almacenamiento en memoria a través de un comando **Archivo Abrir**.  Vuelven a escribir el archivo actualizado en el medio de almacenamiento al mismo tiempo con un comando **Guardar archivo** o **Guardar como**.  Lo que el usuario ve es un archivo de datos.  
  
 Algunas categorías de aplicaciones, sin embargo, no requieren un documento.  Las aplicaciones de base de datos funcionan basándose en transacciones.  La aplicación selecciona registros de una base de datos y los presenta al usuario, con frecuencia uno a la vez.  Lo que el usuario suele ver es un solo registro activo, que puede ser el único existente en la memoria.  
  
 Si la aplicación no requiere un documento para almacenar datos, se puede omitir parte o toda la arquitectura documento\/vista del marco de trabajo.  La proporción en que se prescinda de ella dependerá del enfoque elegido.  Se puede:  
  
-   Usar un documento mínimo como lugar para almacenar una conexión al origen de datos y prescindir de algunas características habituales de los documentos, como la serialización.  Es útil si se desea tener varias vistas de los datos y sincronizarlas todas, actualizándolas a la vez, etc.  
  
-   Utilizar una ventana de marco, en la que se dibuja directamente en lugar de usar una vista.  En este caso, se omite el documento y se almacenan los datos o las conexiones de datos en los objetos de la ventana de marco.  
  
##  <a name="_core_appwizard_options_for_documents_and_views"></a> Opciones del Asistente para aplicaciones para documentos y vistas  
 El Asistente para aplicaciones MFC tiene varias opciones en **Seleccionar compatibilidad con bases de datos**, que se detallan en la siguiente tabla.  Si utiliza el asistente para crear una aplicación, todas estas opciones producen aplicaciones con documentos y vistas.  Algunas opciones proporcionan documentos y vistas que omiten la funcionalidad del documento no requerida.  Para obtener más información, vea [Compatibilidad con bases de datos, Asistente para aplicaciones MFC](../mfc/reference/database-support-mfc-application-wizard.md).  
  
|Opción|View|Documento|  
|------------|----------|---------------|  
|**None**|Se deriva de `CView`.|No proporciona compatibilidad con bases de datos.  Ésta es la opción predeterminada.<br /><br /> Si selecciona la opción **Compatibilidad con la arquitectura documento\/vista** en la página [Tipo de aplicación, Asistente para aplicaciones MFC](../mfc/reference/application-type-mfc-application-wizard.md), obtendrá compatibilidad total con documentos, incluida la serialización y los comandos `New`, **Abrir**, **Guardar** y **Guardar como** del menú **Archivo**.  Vea [Aplicaciones sin documentos](#_core_applications_with_no_document).|  
|**Sólo archivos de encabezado**|Se deriva de `CView`.|Proporciona el nivel básico de compatibilidad con bases de datos para la aplicación.<br /><br /> Incluye Afxdb.h.  Agrega bibliotecas de vínculos, pero no crea clases específicas de bases de datos.  Puede crear conjuntos de registros posteriormente y utilizarlos para examinar y actualizar registros.|  
|**Vista de base de datos sin compatibilidad con archivos**|Derivada de `CRecordView`.|Proporciona compatibilidad con documentos pero no con la serialización.  El documento puede almacenar el conjunto de registros y coordinar varias vistas, pero no admite serialización ni los comandos `New`, **Abrir**, **Guardar** ni **Guardar como**.  Vea [Aplicaciones con documentos mínimos](#_core_applications_with_minimal_documents).  Si elige incluir una vista de base de datos, debe especificar el origen de los datos.<br /><br /> Incluye archivos de encabezado de base de datos, bibliotecas de vínculos, una vista y un conjunto de registros. Sólo está disponible para aplicaciones que tengan seleccionada la opción **Compatibilidad con la arquitectura documento\/vista** en la página [Tipo de aplicación, Asistente para aplicaciones MFC](../mfc/reference/application-type-mfc-application-wizard.md).|  
|**Vista de base de datos con compatibilidad con archivos**|Derivada de `CRecordView`.|Proporciona compatibilidad total con documentos, incluida la serialización y los comandos del menú **Archivo** relativos a los documentos.  Las aplicaciones de base de datos suelen funcionar registro a registro, en lugar de archivo a archivo, por lo que no necesitan la serialización.  Sin embargo, es posible que tenga una necesidad especial de la serialización.  Vea [Aplicaciones con documentos mínimos](#_core_applications_with_minimal_documents).  Si elige incluir una vista de base de datos, debe especificar el origen de los datos.<br /><br /> Incluye archivos de encabezado de base de datos, bibliotecas de vínculos, una vista y un conjunto de registros. Sólo está disponible para aplicaciones que tengan seleccionada la opción **Compatibilidad con la arquitectura documento\/vista** en la página [Tipo de aplicación, Asistente para aplicaciones MFC](../mfc/reference/application-type-mfc-application-wizard.md).|  
  
 Para obtener un análisis de alternativas a la serialización y usos alternativos para la serialización, vea [Serialización: Serialización frente a entrada\/salida de bases de datos](../mfc/serialization-serialization-vs-database-input-output.md).  
  
##  <a name="_core_applications_with_minimal_documents"></a> Aplicaciones con documentos mínimos  
 El Asistente para aplicaciones MFC tiene dos opciones que admiten las aplicaciones de acceso a datos basadas en formularios.  Cada opción crea una clase de vista derivada de `CRecordView` y un documento.  Se diferencian en lo que dejan fuera del documento.  
  
###  <a name="_core_a_document_without_file_support"></a> Documento sin compatibilidad con archivos  
 Seleccione la opción **Vista de base de datos sin compatibilidad con archivos** en el asistente para aplicaciones si no necesita la serialización de documentos.  El documento sirve a los siguientes propósitos de utilidad:  
  
-   Es una ubicación adecuada para almacenar un objeto `CRecordset`.  
  
     Este uso refleja los usos habituales de los documentos: el documento almacena los datos \(o en este caso, un conjunto de registros\) y la vista es una vista del documento.  
  
-   Si la aplicación presenta múltiples vistas \(como por ejemplo múltiples vistas de registros\), utilizar un documento permite coordinarlas.  
  
     Si varias vistas muestran los mismos datos, se puede utilizar la función miembro `CDocument::UpdateAllViews` para coordinar las actualizaciones de todas las vistas cuando en una de ellas se modifican los datos.  
  
 Normalmente se utiliza esta opción para aplicaciones sencillas basadas en formularios.  El Asistente para aplicaciones MFC permite el uso de una estructura eficaz para este tipo de aplicaciones, de manera automática.  
  
###  <a name="_core_a_document_with_file_support"></a> Documento con compatibilidad con archivos  
 Seleccione la opción **Vista de base de datos con compatibilidad con archivos** en el Asistente para aplicaciones cuando tenga un uso alternativo para los comandos del menú **Archivo** relacionados con documentos y la serialización de documentos.  En la parte de acceso a datos del programa, se puede utilizar un documento de la misma forma que se describe en [Documento sin compatibilidad con archivos](#_core_a_document_without_file_support).  También es posible usar la capacidad de serialización del documento, por ejemplo, para leer y escribir un documento de perfil de usuario serializado que almacene las preferencias del usuario o cualquier otra información útil.  Para obtener más ideas, vea [Serialización: Serialización frente a entrada\/salida de bases de datos](../mfc/serialization-serialization-vs-database-input-output.md).  
  
 El Asistente para aplicaciones MFC admite esta opción, pero se debe escribir el código que serializa el documento.  Almacene la información serializada en miembros de datos de documento.  
  
##  <a name="_core_applications_with_no_document"></a> Aplicaciones sin documentos  
 A veces se desea crear una aplicación que no utilice documentos ni vistas.  Sin la presencia de documentos, los datos \(como por ejemplo un objeto `CRecordset`\) se almacenan en la clase de ventana de marco o en la clase de aplicación.  Cualquier otro argumento adicional depende de si la aplicación posee interfaz de usuario.  
  
###  <a name="_core_database_support_with_a_user_interface"></a> Compatibilidad con bases de datos con interfaz de usuario  
 Si nuestra aplicación dispone de interfaz de usuario \(que no sea, por ejemplo, una línea de comandos de consola\), dibujará los datos directamente en el área cliente de la ventana de marco en lugar de hacerlo en una vista.  Una aplicación de este tipo no utiliza `CRecordView`, `CFormView` ni `CDialog` para la interfaz de usuario principal, sino que se suele utilizar`CDialog` para los cuadros de diálogo normales.  
  
###  <a name="_core_writing_applications_without_documents"></a> Crear aplicaciones sin documentos  
 El Asistente para aplicaciones no admite la creación de aplicaciones sin documentos; por tanto, debe crear su propia clase derivada de `CWinApp` y, en caso necesario, también una clase `CFrameWnd` o `CMDIFrameWnd`.  Reemplace `CWinApp::InitInstance` y declare un objeto de aplicación como:  
  
```  
CYourNameApp theApp;  
```  
  
 El marco de trabajo proporciona el mecanismo de mapa de mensajes y muchas otras características.  
  
###  <a name="_core_database_support_separate_from_the_user_interface"></a> Compatibilidad con bases de datos independiente de la interfaz de usuario  
 Algunas aplicaciones no necesitan interfaz de usuario, o un uso mínimo de ésta.  Por ejemplo, supongamos que creamos:  
  
-   Un objeto intermedio de acceso a datos al que otras aplicaciones \(clientes\) llaman para el procesamiento especial de datos entre la aplicación y el origen de datos.  
  
-   Una aplicación que procesa datos sin intervención del usuario, como una aplicación que mueve datos de un formato de base de datos a otro u otra que realiza cálculos y actualizaciones por lotes.  
  
 Debido a que ningún documento es el propietario de los objetos `CRecordset` o `CDaoRecordset`, probablemente sea conveniente almacenarlos como miembro de datos incrustado en la clase de aplicación derivada de `CWinApp`.  Las alternativas comprenden:  
  
-   No mantener ningún objeto `CRecordset` o `CDaoRecordset` permanente.  Se puede pasar **NULL** a los constructores de clases de conjunto de registros.  En ese caso, el marco de trabajo crea un objeto `CDatabase` o `CDaoDatabase` temporal con la información de la función miembro `GetDefaultConnect` del conjunto de registros.  Éste es el enfoque alternativo más probable.  
  
-   Hacer del objeto `CRecordset` o `CDaoRecordset` una variable global.  Esta variable debe ser un puntero a un objeto de conjunto de registros que se crea dinámicamente al reemplazar `CWinApp::InitInstance`.  De esta forma, se evita el intento de construir el objeto antes de que se inicialice el marco de trabajo.  
  
-   Utilizar objetos de conjunto de registros al igual que se haría en el contexto de un documento o vista.  Crear conjuntos de registros en las funciones miembro de los objetos de aplicación o ventana de marco.  
  
## Vea también  
 [Clases de base de datos MFC \(ODBC y DAO\)](../data/mfc-database-classes-odbc-and-dao.md)