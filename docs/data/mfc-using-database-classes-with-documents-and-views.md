---
title: 'MFC: Utilizar clases de base de datos con documentos y vistas | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- documents [C++], database applications
- recordsets [C++], documents and views
- CRecordView class, using in database forms
- views [C++], database applications
- forms [C++], database applications
- record views [C++], form-based applications
- document/view architecture [C++], in databases
- database applications [C++], forms
- database classes [C++], MFC
- ODBC recordsets [C++], documents and views
- ODBC [C++], forms
ms.assetid: 83979974-fc63-46ac-b162-e8403a572e2c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6d3e2286c10d83b25576474692b5a7faeb9bb332
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC: Utilizar clases de base de datos con documentos y vistas
Puede utilizar las clases de base de datos MFC con o sin la arquitectura documento/vista. Trabajar con documentos y vistas hace hincapié en este tema. Se explica:  
  
-   [Cómo escribir una aplicación basada en formularios](#_core_writing_a_form.2d.based_application) mediante un `CRecordView` objeto como la vista principal en el documento.  
  
-   [Cómo utilizar objetos de conjunto de registros en sus documentos y vistas](#_core_using_recordsets_in_documents_and_views).  
  
-   [Otras consideraciones](#_core_other_factors).  
  
 Para alternativas, consulte [MFC: utilizar clases de base de datos sin documentos ni vistas](../data/mfc-using-database-classes-without-documents-and-views.md).  
  
##  <a name="_core_writing_a_form.2d.based_application"></a>Escribir una aplicación basada en formularios  
 Muchas aplicaciones de acceso a datos se basan en formularios. La interfaz de usuario es un formulario que contenga controles en el que el usuario examina, escribe o edita datos. Para que la aplicación basada en formularios, use la clase `CRecordView`. Al ejecutar el Asistente para aplicaciones MFC y seleccione **ODBC** tipo de cliente en el **compatibilidad de base de datos** página, el proyecto utiliza `CRecordView` para la clase de vista.
  
 En una aplicación basada en formularios, cada objeto de vista de registros almacena un puntero a un `CRecordset` objeto. Mecanismo de intercambio (RFX) de campos de registros del marco de trabajo intercambia datos entre el conjunto de registros y el origen de datos. Los datos de cuadro de diálogo (DDX) mecanismo intercambia datos entre los miembros de datos de campo del objeto de conjunto de registros y los controles en el formulario de exchange. `CRecordView`También proporciona predeterminado funciones del controlador de comandos para navegar por los registros en el formulario.  
  
 Para crear una aplicación basada en formularios con el Asistente para aplicaciones, consulte [crear una aplicación MFC basada en formularios](../mfc/reference/creating-a-forms-based-mfc-application.md) y [compatibilidad de base de datos, Asistente para aplicaciones MFC](../mfc/reference/database-support-mfc-application-wizard.md).  
  
 Para obtener una explicación completa de los formularios, consulte [vistas de registros](../data/record-views-mfc-data-access.md).  
  
##  <a name="_core_using_recordsets_in_documents_and_views"></a>Usar conjuntos de registros en documentos y vistas  
 Muchas aplicaciones sencillas basadas en formularios no es necesario documentos. Si la aplicación es más compleja, probablemente desee utilizar un documento como un proxy para la base de datos, almacenando un `CDatabase` objeto que se conecta al origen de datos. Las aplicaciones basadas en formularios suelen almacenan un puntero a un objeto de conjunto de registros en la vista. Otros tipos de aplicaciones de base de datos almacenan conjuntos de registros y `CDatabase` objeto en el documento. Estas son algunas posibilidades para usar los documentos en aplicaciones de base de datos:  
  
-   Si se obtiene acceso a un conjunto de registros en un contexto local, cree un `CRecordset` objeto localmente en funciones miembro del documento o la vista, según sea necesario.  
  
     Declare un objeto de conjunto de registros como una variable local en una función. Pasar **NULL** al constructor, lo que hace que el marco de trabajo crear y abrir un archivo temporal `CDatabase` objeto automáticamente. Como alternativa, se puede pasar un puntero a un `CDatabase` objeto. Utilice el conjunto de registros dentro de la función y permita que se destruya automáticamente cuando finaliza la función.  
  
     Cuando se pasa **NULL** a un constructor de conjunto de registros, el marco de trabajo utiliza la información devuelta por el conjunto de registros `GetDefaultConnect` función de miembro para crear un `CDatabase` de objeto y ábralo. Los asistentes implementan `GetDefaultConnect` para usted.  
  
-   Si se obtiene acceso a un conjunto de registros durante la vida del documento, se deben insertar uno o varios `CRecordset` objetos en el documento.  
  
     Crear los objetos de conjunto de registros al inicializar el documento o según sea necesario. Puede escribir una función que devuelve un puntero al conjunto de registros si ya existe o construye y abre el conjunto de registros si aún no existe. Cerrar, eliminar y volver a crear el conjunto de registros según sea necesario o llamar a su **Requery** función de miembro para actualizar los registros.  
  
-   Si se obtiene acceso a un origen de datos durante la vigencia del documento, se deben insertar un `CDatabase` de un objeto o almacenar un puntero a un `CDatabase` objeto en ella.  
  
     La `CDatabase` objeto administra una conexión al origen de datos. El objeto se crea automáticamente durante la construcción de documento y se llama a su **abiertos** función de miembro al inicializar el documento. Al crear objetos de conjunto de registros en funciones miembro de documento, debe pasar un puntero para el documento `CDatabase` objeto. Así asocia cada conjunto de registros con su origen de datos. El objeto de base de datos normalmente se destruye cuando se cierra el documento. Normalmente, los objetos de conjunto de registros se destruyen cuando sale del ámbito de una función.  
  
##  <a name="_core_other_factors"></a>Otros factores  
 Las aplicaciones basadas en formularios a menudo no tiene ningún uso para el mecanismo de serialización del documento del marco de trabajo, por lo que puede que quiera quitar, deshabilitar o reemplazar la `New` y **abiertos** comandos en el **archivo**menú. Vea el artículo [serialización: serialización frente. Base de datos de entrada/salida](../mfc/serialization-serialization-vs-database-input-output.md).  
  
 También puede hacer uso de las muchas posibilidades de interfaz de usuario que puede admitir el marco de trabajo. Por ejemplo, podría utilizar varios `CRecordView` objetos en una ventana divisora, abrir múltiples conjuntos de registros en diferentes varias ventanas de documento MDI (interfaz) secundarias y así sucesivamente.  
  
 Puede implementar la impresión de cualquier objeto almacenado en la vista, ya sea un formulario se implementa con `CRecordView` u otra cosa. Como las clases derivadas de `CFormView`, `CRecordView` admite la impresión, pero puede invalidar el `OnPrint` función de miembro para permitir la impresión. Para obtener más información, vea la clase [CFormView](../mfc/reference/cformview-class.md).  
  
 No puede usar en todos los documentos y vistas. En ese caso, consulte [MFC: utilizar clases de base de datos sin documentos ni vistas](../data/mfc-using-database-classes-without-documents-and-views.md).  
  
## <a name="see-also"></a>Vea también  
 [Las clases de base de datos MFC (.. / data/mfc-database-classes-odbc-and-dao.md)