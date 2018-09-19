---
title: 'MFC: Utilizar clases de base de datos con documentos y vistas | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0fcb0f6f40ac9577813463a4aa3f6265df938511
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094837"
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC: Utilizar clases de base de datos con documentos y vistas

Puede usar las clases de base de datos MFC con o sin la arquitectura documento/vista. En este tema se destaca cómo trabajar con documentos y vistas. Explica:  
  
- [Cómo escribir una aplicación basada en formularios](#_core_writing_a_form.2d.based_application) mediante un `CRecordView` objeto como la vista principal en el documento.  
  
- [Cómo utilizar objetos de conjunto de registros en sus documentos y vistas](#_core_using_recordsets_in_documents_and_views).  
  
- [Otras consideraciones](#_core_other_factors).  
  
Para alternativas, consulte [MFC: utilizar clases de base de datos sin documentos y vistas](../data/mfc-using-database-classes-without-documents-and-views.md).  
  
##  <a name="_core_writing_a_form.2d.based_application"></a> Escribir una aplicación basada en formularios  

Muchas aplicaciones de acceso a datos se basan en formularios. La interfaz de usuario es un formulario que contiene los controles en el que el usuario examina, entra o edita datos. Para hacer que su aplicación basada en formularios, utilice la clase `CRecordView`. Al ejecutar el Asistente para aplicaciones MFC y seleccione **ODBC** tipo de cliente en el **soporte técnico de la base de datos** página, el proyecto usa `CRecordView` para la clase de vista.
  
En una aplicación basada en formularios, cada objeto de vista de registros almacena un puntero a un `CRecordset` objeto. Mecanismo de intercambio (RFX) de campos de registros de .NET framework intercambia datos entre el conjunto de registros y el origen de datos. Los datos de cuadro de diálogo (DDX) mecanismo intercambia datos entre los miembros de datos de campo del objeto recordset y los controles del formulario de exchange. `CRecordView` También proporciona predeterminada funciones del controlador de comandos para navegar por los registros en el formulario.  
  
Para crear una aplicación basada en formularios con el Asistente para aplicaciones, consulte [crear una aplicación MFC basada en formularios](../mfc/reference/creating-a-forms-based-mfc-application.md) y [soporte técnico de la base de datos, Asistente para aplicaciones MFC](../mfc/reference/database-support-mfc-application-wizard.md).  
  
Para ver una explicación detallada de los formularios, consulte [vistas de registros](../data/record-views-mfc-data-access.md).  
  
##  <a name="_core_using_recordsets_in_documents_and_views"></a> Usar conjuntos de registros en documentos y vistas  

Muchas aplicaciones sencillas basadas en formularios no es necesario documentos. Si la aplicación es más compleja, probablemente desee usar un documento como un proxy para la base de datos, almacenando un `CDatabase` objeto que se conecta al origen de datos. Las aplicaciones basadas en formularios suelen almacenan un puntero a un objeto de conjunto de registros en la vista. Otros tipos de aplicaciones de base de datos almacenan conjuntos de registros y `CDatabase` objeto en el documento. Estas son algunas posibilidades de uso de documentos en aplicaciones de base de datos:  
  
- Si tiene acceso a un conjunto de registros en un contexto local, cree un `CRecordset` objeto localmente en funciones miembro del documento o la vista, según sea necesario.  
  
     Declare un objeto de conjunto de registros como una variable local en una función. Pasar NULL al constructor, lo que hace que el marco de trabajo crear y abrir un archivo temporal `CDatabase` objeto automáticamente. Como alternativa, puede pasar un puntero a un `CDatabase` objeto. Utilice el conjunto de registros dentro de la función y permita que se destruya automáticamente cuando finaliza la función.  
  
     Cuando se pasa NULL a un constructor de conjunto de registros, el marco de trabajo utiliza la información devuelta por el conjunto de registros `GetDefaultConnect` función miembro para crear un `CDatabase` de objeto y ábralo. Los asistentes implementan `GetDefaultConnect` para usted.  
  
- Si tiene acceso a un conjunto de registros durante la vigencia del documento, insertar uno o varios `CRecordset` objetos del documento.  
  
     Crear los objetos de conjunto de registros al inicializar el documento o según sea necesario. Puede escribir una función que devuelve un puntero al conjunto de registros si ya existe o crea y abre el conjunto de registros si aún no existe. Cerrar, eliminar y volver a crear el conjunto de registros según sea necesario o llamar a su `Requery` función miembro para actualizar los registros.  
  
- Si tiene acceso a un origen de datos durante la vigencia del documento, insertar un `CDatabase` de objeto o almacenar un puntero a un `CDatabase` objeto en él.  
  
     La `CDatabase` objeto administra una conexión al origen de datos. El objeto se crea automáticamente durante la construcción de documento y se llama a su `Open` función de miembro al inicializar el documento. Al crear objetos de conjunto de registros en funciones miembro de documento, pasar un puntero al documento `CDatabase` objeto. Esto asocia cada conjunto de registros a su origen de datos. Normalmente, se destruye el objeto de base de datos cuando se cierra el documento. Normalmente, los objetos de conjunto de registros se destruyen cuando cierre el ámbito de una función.  
  
##  <a name="_core_other_factors"></a> Otros factores  

Aplicaciones basadas en formularios a menudo no tienen ningún uso para el mecanismo de serialización de documentos de .NET framework, por lo que es posible que desee quitar, deshabilitar o reemplazar el **New** y **abierto** comandos en el **Archivo** menú. Consulte el artículo [serialización: serialización frente. Base de datos de entrada/salida](../mfc/serialization-serialization-vs-database-input-output.md).  
  
También puede hacer uso de las muchas posibilidades de interfaz de usuario que puede admitir el marco de trabajo. Por ejemplo, podría utilizar varios `CRecordView` objetos en una ventana divisora, abrir múltiples conjuntos de registros en diferentes varias ventanas de documento MDI (interfaz) secundarias y así sucesivamente.  
  
Es posible que desee implementar la impresión de cualquier cosa que esté en la vista, ya sea un formulario se implementa con `CRecordView` o alguna otra cosa. Como las clases derivadas de `CFormView`, `CRecordView` no admita la impresión, pero puede invalidar el `OnPrint` la función miembro se permite la impresión. Para obtener más información, vea la clase [CFormView](../mfc/reference/cformview-class.md).  
  
Es posible que no desea utilizar documentos y vistas en absoluto. En ese caso, consulte [MFC: utilizar clases de base de datos sin documentos y vistas](../data/mfc-using-database-classes-without-documents-and-views.md).  
  
## <a name="see-also"></a>Vea también  

[Las clases de base de datos MFC (.. / data/mfc-database-classes-odbc-and-dao.md)