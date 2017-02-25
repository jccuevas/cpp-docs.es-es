---
title: "MFC: Utilizar clases de base de datos con documentos y vistas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoRecordView (clase), utilizar en aplicaciones de bases de datos"
  - "CDaoRecordView (clase), utilizar en formularios de bases de datos"
  - "CRecordView (clase), utilizar en formularios de bases de datos"
  - "DAO [C++], formularios en aplicaciones de bases de datos"
  - "conjuntos de registros DAO [C++]"
  - "conjuntos de registros DAO [C++], documentos y vistas"
  - "aplicaciones de base de datos [C++], formularios"
  - "clases de base de datos [C++], MFC"
  - "arquitectura documento/vista [C++], en bases de datos"
  - "documentos [C++], aplicaciones de base de datos"
  - "formularios [C++], aplicaciones de base de datos"
  - "ODBC [C++], formularios"
  - "conjuntos de registros ODBC [C++], documentos y vistas"
  - "vistas de registros [C++], aplicaciones basadas en formularios"
  - "conjuntos de registros [C++], documentos y vistas"
  - "vistas [C++], aplicaciones de base de datos"
ms.assetid: 83979974-fc63-46ac-b162-e8403a572e2c
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# MFC: Utilizar clases de base de datos con documentos y vistas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se pueden utilizar las clases de base de datos MFC \(DAO u ODBC\) con o sin la arquitectura documento\/vista.  Este tema resalta la manera de trabajar con documentos y vistas.  Explica:  
  
-   [Cómo crear una aplicación basada en formularios](#_core_writing_a_form.2d.based_application) utilizando un objeto `CRecordView` o `CDaoRecordView` como vista principal del documento.  
  
-   [Cómo utilizar objetos de conjuntos de registros en documentos y vistas](#_core_using_recordsets_in_documents_and_views).  
  
-   [Otras consideraciones](#_core_other_factors).  
  
 Para consultar otras alternativas, vea [MFC: Utilizar clases de base de datos sin documentos ni vistas](../data/mfc-using-database-classes-without-documents-and-views.md).  
  
##  <a name="_core_writing_a_form.2d.based_application"></a> Cómo crear una aplicación basada en formularios  
 Numerosas aplicaciones de acceso a datos están basadas en formularios.  La interfaz de usuario consiste en un formulario que contiene controles en los cuales el usuario examina, escribe o modifica datos.  Para crear una aplicación basada en formularios, utilice las clases `CRecordView` o `CDaoRecordView`.  Al ejecutar el Asistente para aplicaciones MFC y seleccionar el tipo de cliente **ODBC** en la página **Compatibilidad con bases de datos**, el proyecto utiliza `CRecordView` como clase de vista.  Los asistentes ya no son compatibles con DAO, por lo que, para utilizar `CDaoRecordView`, es necesario escribir el código manualmente.  
  
 En una aplicación basada en formularios, cada objeto de vista de registro almacena un puntero a un objeto `CRecordset` o `CDaoRecordset`.  El mecanismo de intercambio de campos de registro \(RFX\) del marco de trabajo MFC intercambia datos entre el conjunto de registros y el origen de datos.  El mecanismo de intercambio de datos de cuadro de diálogo \(DDX\) intercambia datos entre los miembros de datos de campo del objeto de conjunto de registros y los controles del formulario.  `CRecordView` o `CDaoRecordView` también proporcionan funciones de controlador de comandos predeterminadas para navegar entre los registros del formulario.  
  
 Para crear una aplicación basada en formularios mediante el asistente para aplicaciones, vea [Crear una aplicación MFC basada en formularios](../mfc/reference/creating-a-forms-based-mfc-application.md) y [Compatibilidad con bases de datos, Asistente para aplicaciones MFC](../mfc/reference/database-support-mfc-application-wizard.md).  
  
 Para leer una descripción detallada de los formularios, vea [Vistas de registros](../data/record-views-mfc-data-access.md).  
  
##  <a name="_core_using_recordsets_in_documents_and_views"></a> Utilizar conjuntos de registros en documentos y vistas  
 Muchas aplicaciones sencillas basadas en formularios no necesitan el uso de documentos.  Si la aplicación es más compleja, probablemente desee utilizar un documento como proxy para la base de datos, almacenando un objeto `CDatabase` o `CDaoDatabase` que se conecte al origen de datos.  Las aplicaciones basadas en formularios suelen almacenar un puntero a un objeto de conjunto de registros en la vista.  Otros tipos de aplicaciones de base de datos almacenan conjuntos de registros y los objetos `CDatabase` o `CDaoDatabase` en el documento.  A continuación se detallan algunas posibilidades a la hora de usar documentos en aplicaciones de base de datos:  
  
-   Si obtiene acceso a un conjunto de registros en un contexto local, cree los objetos `CRecordset` o `CDaoRecordset` localmente en funciones miembro del documento o de la vista, según convenga.  
  
     Declarar un objeto de conjunto de registros como variable local en una función.  Para ello, pase **NULL** al constructor, lo que hace que el marco de trabajo cree y abra un objeto temporal `CDatabase` o `CDaoDatabase`.  Como alternativa, se puede pasar un puntero a un objeto `CDatabase` o `CDaoDatabase`.  Use el conjunto de registros dentro de la función y permita que se destruya automáticamente cuando termine de ejecutarse la función.  
  
     Al pasar **NULL** a un constructor de conjunto de registros, el marco de trabajo utiliza la información devuelta por la función miembro `GetDefaultConnect` del conjunto de registros para crear un objeto `CDatabase` o `CDaoDatabase` y abrirlo.  Los asistentes implementan `GetDefaultConnect`.  
  
-   Si se obtiene acceso a un conjunto de registros mientras dure el documento, se deben insertar uno o varios objetos `CRecordset` o `CDaoRecordset` en el documento.  
  
     Construya los objetos de conjunto de registros al inicializar el documento o según sea necesario.  Se puede crear una función que devuelva un puntero a este conjunto de registros si ya existe, o cree y abra el conjunto de registros si aún no existe.  Cierre, elimine y vuelva a crear el conjunto de registros según lo necesite o llame a su función miembro **Requery** para actualizar los registros.  
  
-   Si obtiene acceso a un origen de datos mientras dure el documento, inserte un objeto `CDatabase` o `CDaoDatabase` o almacene en él un puntero a un objeto `CDatabase` o `CDaoDatabase`.  
  
     El objeto `CDatabase` o `CDaoDatabase` administra una conexión al origen de datos.  El objeto se crea automáticamente durante la construcción del documento, y debe llamar a su función miembro **Open** al inicializar el documento.  Al crear objetos de conjunto de registros en funciones miembro de documentos, se debe pasar un puntero al objeto `CDatabase` o `CDaoDatabase` del documento.  Al hacerlo se asocia cada conjunto de registros con su origen de datos respectivo.  El objeto de base de datos se destruye normalmente cuando se cierra el documento.  Los objetos de conjunto de registros suelen destruirse al salir del ámbito de una función.  
  
##  <a name="_core_other_factors"></a> Otros factores  
 Las aplicaciones basadas en formularios a menudo no utilizan el mecanismo de serialización del marco de trabajo del documento, por lo que puede resultar conveniente quitar, deshabilitar o reemplazar los comandos `New` y **Abrir** del menú **Archivo**.  Vea el artículo [Serialización: serialización frente a entrada\/salida de bases de datos](../mfc/serialization-serialization-vs-database-input-output.md).  
  
 También puede ser conveniente utilizar las numerosas posibilidades de la interfaz de usuario que admite el marco de trabajo.  Por ejemplo, se pueden utilizar varios objetos `CRecordView` o `CDaoRecordView` en una ventana divisora, abrir múltiples conjuntos de registros en diferentes ventanas secundarias MDI \(interfaz de múltiples documentos\), etc.  
  
 Es posible que desee implementar la impresión del contenido de la vista, ya se trate de un formulario implementado con `CRecordView`, con `CDaoRecordView` o de cualquier otra forma.  Al ser clases derivadas de `CFormView`, `CRecordView` y `CDaoRecordView` no admiten la impresión, pero se puede reemplazar la función miembro `OnPrint` para permitir la impresión.  Para obtener más información, vea la clase [CFormView](../mfc/reference/cformview-class.md).  
  
 También es posible que no desee usar documentos ni vistas.  En ese caso, vea [MFC: Utilizar clases de base de datos sin documentos ni vistas](../data/mfc-using-database-classes-without-documents-and-views.md).  
  
## Vea también  
 [Clases de base de datos MFC \(ODBC y DAO\)](../data/mfc-database-classes-odbc-and-dao.md)