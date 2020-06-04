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
ms.openlocfilehash: 9e071e0cc25492073cd74ed517284476b6e49ef8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368897"
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC: Utilizar clases de base de datos con documentos y vistas

Puede utilizar las clases de base de datos MFC con o sin la arquitectura de documento/vista. En este tema se hace hincapié en trabajar con documentos y vistas. Explica:

- [Cómo escribir una aplicación basada](#_core_writing_a_form.2d.based_application) `CRecordView` en formularios utilizando un objeto como vista principal del documento.

- Cómo utilizar objetos de conjunto de [registros en los documentos y vistas.](#_core_using_recordsets_in_documents_and_views)

- [Otras consideraciones](#_core_other_factors).

Para obtener alternativas, vea MFC: Uso de clases de base de datos [sin documentos y vistas](../data/mfc-using-database-classes-without-documents-and-views.md).

## <a name="writing-a-form-based-application"></a><a name="_core_writing_a_form.2d.based_application"></a>Escribir una solicitud basada en formularios

Muchas aplicaciones de acceso a datos se basan en formularios. La interfaz de usuario es un formulario que contiene controles en los que el usuario examina, introduce o edita datos. Para que el formulario de `CRecordView`solicitud se base en, utilice la clase . Al ejecutar el Asistente para aplicaciones MFC y seleccionar el tipo `CRecordView` de cliente **ODBC** en la página Compatibilidad con **bases** de datos, el proyecto se usa para la clase de vista.

En una aplicación basada en formularios, cada objeto `CRecordset` de vista de registro almacena un puntero a un objeto. El mecanismo de intercambio de campos de registros (RFX) del marco de trabajo intercambia datos entre el conjunto de registros y el origen de datos. El mecanismo de intercambio de datos de cuadro de diálogo (DDX) intercambia datos entre los miembros de datos de campo del objeto de conjunto de registros y los controles del formulario. `CRecordView`También proporciona funciones de controlador de comandos predeterminadas para navegar de un registro a otro en el formulario.

Para crear una aplicación basada en formularios con el Asistente para aplicaciones, vea [Creación de una aplicación MFC basada en formularios](../mfc/reference/creating-a-forms-based-mfc-application.md) y compatibilidad con bases de [datos, Asistente para aplicaciones MFC](../mfc/reference/database-support-mfc-application-wizard.md).

Para obtener una explicación completa de los formularios, vea Vistas de [registros](../data/record-views-mfc-data-access.md).

## <a name="using-recordsets-in-documents-and-views"></a><a name="_core_using_recordsets_in_documents_and_views"></a>Uso de conjuntos de registros en documentos y vistas

Muchas aplicaciones simples basadas en formularios no necesitan documentos. Si la aplicación es más compleja, es probable que desee usar `CDatabase` un documento como proxy para la base de datos, almacenando un objeto que se conecta al origen de datos. Las aplicaciones basadas en formularios suelen almacenar un puntero a un objeto de conjunto de registros en la vista. Otros tipos de aplicaciones de `CDatabase` base de datos almacenan conjuntos de registros y objetos en el documento. Estas son algunas posibilidades para utilizar documentos en aplicaciones de base de datos:

- Si tiene acceso a un conjunto de `CRecordset` registros en un contexto local, cree un objeto localmente en las funciones miembro del documento o la vista, según sea necesario.

   Declare un objeto de conjunto de registros como una variable local en una función. Pase NULL al constructor, lo que hace que `CDatabase` el marco de trabajo para crear y abrir un objeto temporal para usted. Como alternativa, pase un `CDatabase` puntero a un objeto. Utilice el conjunto de registros dentro de la función y deje que se destruya automáticamente cuando se cierre la función.

   Cuando se pasa NULL a un constructor de conjunto de `GetDefaultConnect` registros, `CDatabase` el marco de trabajo utiliza la información devuelta por la función miembro del conjunto de registros para crear un objeto y abrirlo. Los asistentes `GetDefaultConnect` se implementan por usted.

- Si tiene acceso a un conjunto de registros `CRecordset` durante la duración del documento, incruste uno o varios objetos en el documento.

   Construya los objetos de conjunto de registros al inicializar el documento o según sea necesario. Puede escribir una función que devuelva un puntero al conjunto de registros si ya existe o construye y abre el conjunto de registros si aún no existe. Cierre, elimine y vuelva a crear el `Requery` conjunto de registros según sea necesario, o llame a su función miembro para actualizar los registros.

- Si tiene acceso a un origen de datos `CDatabase` durante la duración del `CDatabase` documento, incruste un objeto o almacene un puntero a un objeto en él.

   El `CDatabase` objeto administra una conexión con el origen de datos. El objeto se construye automáticamente durante la `Open` construcción del documento y se llama a su función miembro al inicializar el documento. Al construir objetos de conjunto de registros en funciones miembro de documento, se pasa un puntero al objeto del `CDatabase` documento. Esto asocia cada conjunto de registros con su origen de datos. Normalmente, el objeto de base de datos se destruye cuando se cierra el documento. Los objetos de conjunto de registros normalmente se destruyen cuando salen del ámbito de una función.

## <a name="other-factors"></a><a name="_core_other_factors"></a>Otros factores

Las aplicaciones basadas en formularios a menudo no tienen ningún uso para el mecanismo de serialización de documentos del marco de trabajo, por lo que es posible que desee quitar, deshabilitar o reemplazar los comandos **Nuevo** y **Abrir** en el menú **Archivo.** Consulte el artículo [Serialización: serialización frente a entrada/salida](../mfc/serialization-serialization-vs-database-input-output.md)de base de datos .

También es posible que desee hacer uso de las muchas posibilidades de interfaz de usuario que el marco de trabajo puede admitir. Por ejemplo, podría `CRecordView` usar varios objetos en una ventana divisora, abrir varios conjuntos de registros en diferentes ventanas secundarias de interfaz de documentos múltiples (MDI), etc.

Es posible que desee implementar la impresión de lo que `CRecordView` está en su vista, ya sea un formulario implementado con o algo más. Como las clases derivadas de `CFormView`, `CRecordView` no admite `OnPrint` la impresión, pero puede invalidar la función miembro para permitir la impresión. Para obtener más información, vea la clase [CFormView](../mfc/reference/cformview-class.md).

Es posible que no desee utilizar documentos y vistas en absoluto. En ese caso, vea MFC: Uso de clases de base de datos [sin documentos y vistas](../data/mfc-using-database-classes-without-documents-and-views.md).

## <a name="see-also"></a>Consulte también

[Clases de bases de datos MFC](../data/mfc-database-classes-odbc-and-dao.md)
