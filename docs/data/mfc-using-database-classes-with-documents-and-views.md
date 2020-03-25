---
title: 'MFC: Utilizar clases de base de datos con documentos y vistas'
ms.date: 11/04/2016
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
ms.openlocfilehash: e2b073b20b9518667b43c30e7ee3199a84a3ad38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213387"
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC: Utilizar clases de base de datos con documentos y vistas

Puede utilizar las clases de base de datos MFC con o sin la arquitectura documento/vista. En este tema se resalta el trabajo con documentos y vistas. Explica:

- [Cómo escribir una aplicación basada en formularios](#_core_writing_a_form.2d.based_application) con un objeto `CRecordView` como vista principal en el documento.

- [Cómo usar objetos de conjunto de registros en los documentos y vistas](#_core_using_recordsets_in_documents_and_views).

- [Otras consideraciones](#_core_other_factors).

Para ver alternativas, vea [MFC: usar clases de base de datos sin documentos ni vistas](../data/mfc-using-database-classes-without-documents-and-views.md).

##  <a name="writing-a-form-based-application"></a><a name="_core_writing_a_form.2d.based_application"></a>Escribir una aplicación basada en formularios

Muchas aplicaciones de acceso a datos se basan en formularios. La interfaz de usuario es un formulario que contiene controles en los que el usuario examina, introduce o edita datos. Para que el formulario de la aplicación se base, use `CRecordView`de clase. Al ejecutar el Asistente para aplicaciones MFC y seleccionar tipo de cliente **ODBC** en la página **compatibilidad con bases de datos** , el proyecto utiliza `CRecordView` para la clase de vista.

En una aplicación basada en formularios, cada objeto de vista de registros almacena un puntero a un objeto `CRecordset`. El mecanismo de intercambio de campos de registros (RFX) del marco intercambia datos entre el conjunto de registros y el origen de datos. El mecanismo de intercambio de datos de cuadros de diálogo (DDX) intercambia datos entre los miembros de datos de campo del objeto de conjunto de registros y los controles del formulario. `CRecordView` también proporciona funciones de controlador de comandos predeterminadas para navegar desde el registro al registro en el formulario.

Para crear una aplicación basada en formularios con el Asistente para aplicaciones, vea [crear una aplicación MFC basada en formularios](../mfc/reference/creating-a-forms-based-mfc-application.md) y [compatibilidad con bases de datos, Asistente para aplicaciones MFC](../mfc/reference/database-support-mfc-application-wizard.md).

Para obtener una descripción completa de los formularios, consulte [vistas de registros](../data/record-views-mfc-data-access.md).

##  <a name="using-recordsets-in-documents-and-views"></a><a name="_core_using_recordsets_in_documents_and_views"></a>Usar conjuntos de registros en documentos y vistas

Muchas aplicaciones sencillas basadas en formularios no necesitan documentos. Si la aplicación es más compleja, probablemente desee usar un documento como proxy para la base de datos, almacenando un `CDatabase` objeto que se conecta al origen de datos. Las aplicaciones basadas en formularios suelen almacenar un puntero a un objeto de conjunto de registros en la vista. Otros tipos de aplicaciones de base de datos almacenan conjuntos de registros y `CDatabase` objeto en el documento. Estas son algunas posibilidades de uso de documentos en aplicaciones de base de datos:

- Si tiene acceso a un conjunto de registros en un contexto local, cree un `CRecordset` objeto localmente en las funciones miembro del documento o la vista, según sea necesario.

   Declare un objeto de conjunto de registros como una variable local en una función. Pase NULL al constructor, que hace que el marco de trabajo cree y abra un objeto temporal de `CDatabase`. Como alternativa, pase un puntero a un objeto `CDatabase`. Utilice el conjunto de registros dentro de la función y deje que se destruya automáticamente cuando finalice la función.

   Cuando se pasa NULL a un constructor de conjunto de registros, el marco de trabajo usa la información devuelta por la función miembro `GetDefaultConnect` del conjunto de registros para crear un objeto `CDatabase` y abrirlo. Los asistentes implementan `GetDefaultConnect`.

- Si tiene acceso a un conjunto de registros durante la vigencia del documento, inserte uno o más objetos `CRecordset` en el documento.

   Construya los objetos de conjunto de registros al inicializar el documento o según sea necesario. Podría escribir una función que devuelva un puntero al conjunto de registros si ya existe o construye y abre el conjunto de registros si aún no existe. Cierre, elimine y vuelva a crear el conjunto de registros según sea necesario, o llame a su función miembro `Requery` para actualizar los registros.

- Si va a tener acceso a un origen de datos durante el período de duración del documento, inserte un `CDatabase` objeto o almacene un puntero a un objeto `CDatabase` en él.

   El objeto `CDatabase` administra una conexión con el origen de datos. El objeto se crea automáticamente durante la construcción del documento y se llama a su función miembro `Open` al inicializar el documento. Cuando se construyen objetos de conjunto de registros en funciones miembro de documento, se pasa un puntero al objeto `CDatabase` del documento. Esto asocia cada conjunto de registros a su origen de datos. Normalmente, el objeto de base de datos se destruye cuando se cierra el documento. Normalmente, los objetos de conjunto de registros se destruyen cuando salen del ámbito de una función.

##  <a name="other-factors"></a><a name="_core_other_factors"></a>Otros factores

Las aplicaciones basadas en formularios no suelen usarse para el mecanismo de serialización de documentos del marco, por lo que es posible que desee quitar, deshabilitar o reemplazar los comandos **nuevos** y **abrir** en el menú **archivo** . Vea el artículo [serialización: serialización frente a entrada/salida de bases de datos](../mfc/serialization-serialization-vs-database-input-output.md).

Es posible que también desee usar las muchas posibilidades de interfaz de usuario que el marco de trabajo admite. Por ejemplo, podría utilizar varios objetos `CRecordView` en una ventana divisora, abrir varios conjuntos de registros en distintas ventanas secundarias de interfaz de múltiples documentos (MDI), etc.

Es posible que desee implementar la impresión de lo que haya en la vista, ya sea un formulario implementado con `CRecordView` o de otro tipo. Como clases derivadas de `CFormView`, `CRecordView` no admite la impresión, pero puede invalidar la función miembro `OnPrint` para permitir la impresión. Para obtener más información, vea la clase [CFormView](../mfc/reference/cformview-class.md).

Es posible que no desee usar documentos ni vistas en absoluto. En ese caso, vea [MFC: usar clases de base de datos sin documentos ni vistas](../data/mfc-using-database-classes-without-documents-and-views.md).

## <a name="see-also"></a>Consulte también

[Clases de bases de datos MFC](../data/mfc-database-classes-odbc-and-dao.md)
