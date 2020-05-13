---
title: 'Objetos de datos y orígenes de datos: manipulación'
ms.date: 11/04/2016
helpviewer_keywords:
- data objects [MFC], manipulating
- data sources [MFC], data operations
- data sources [MFC], inserting data
- Clipboard [MFC], determining available formats
- OLE [MFC], data objects
- Clipboard [MFC], passing format information
- data sources [MFC], determining available formats
- delayed rendering [MFC]
- OLE [MFC], data sources
ms.assetid: f7f27e77-bb5d-4131-b819-d71bf929ebaf
ms.openlocfilehash: a08b6ff274c73d301c156d65aa56fbecca49128c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370548"
---
# <a name="data-objects-and-data-sources-manipulation"></a>Objetos de datos y orígenes de datos: manipulación

Una vez creado un objeto de datos o un origen de datos, puede realizar varias operaciones comunes en los datos, como insertar y quitar datos, enumerar los formatos en los que se encuentra los datos y mucho más. En este artículo se describen las técnicas necesarias para completar las operaciones más comunes. Contenido de los temas:

- [Insertar datos en un origen de datos](#_core_inserting_data_into_a_data_source)

- [Determinación de los formatos disponibles en un objeto de datos](#_core_determining_the_formats_available_in_a_data_object)

- [Recuperación de datos de un objeto de datos](#_core_retrieving_data_from_a_data_object)

## <a name="inserting-data-into-a-data-source"></a><a name="_core_inserting_data_into_a_data_source"></a>Insertar datos en un origen de datos

La forma en que se insertan los datos en un origen de datos depende de si los datos se suministran inmediatamente o a petición, y en qué medio se suministran. Las posibilidades son las siguientes.

### <a name="supplying-data-immediately-immediate-rendering"></a>Suministro de datos inmediatamente (renderizado inmediato)

- Llame `COleDataSource::CacheGlobalData` repetidamente para cada formato de Portapapeles en el que está proporcionando datos. Pase el formato del Portapapeles que se va a utilizar, un identificador a la memoria que contiene los datos y, opcionalmente, una estructura **FORMATETC** que describe los datos.

     o bien

- Si desea trabajar directamente con estructuras **STGMEDIUM,** llame `COleDataSource::CacheData` en lugar de `COleDataSource::CacheGlobalData` en la opción anterior.

### <a name="supplying-data-on-demand-delayed-rendering"></a>Suministro de datos bajo demanda (renderizado retrasado)

Este es un tema avanzado.

- Llame `COleDataSource::DelayRenderData` repetidamente para cada formato de Portapapeles en el que está proporcionando datos. Pase el formato del Portapapeles que se va a utilizar y, opcionalmente, una estructura **FORMATETC** que describa los datos. Cuando se solicitan los datos, `COleDataSource::OnRenderData`el marco de trabajo llamará a , que debe invalidar.

     o bien

- Si utiliza `CFile` un objeto para proporcionar `COleDataSource::DelayRenderFileData` los `COleDataSource::DelayRenderData` datos, llame en lugar de en la opción anterior. Cuando se solicitan los datos, `COleDataSource::OnRenderFileData`el marco de trabajo llamará a , que debe invalidar.

## <a name="determining-the-formats-available-in-a-data-object"></a><a name="_core_determining_the_formats_available_in_a_data_object"></a>Determinación de los formatos disponibles en un objeto de datos

Antes de que una aplicación permita al usuario pegar datos en ella, necesita saber si hay formatos en el Portapapeles que pueda manejar. Para ello, la aplicación debe hacer lo siguiente:

1. Cree `COleDataObject` un objeto y una estructura **FORMATETC.**

1. Llame a la `AttachClipboard` función miembro del objeto de datos para asociar el objeto de datos con los datos del Portapapeles.

1. Realice una de las siguientes acciones:

   - Llame a la `IsDataAvailable` función miembro del objeto de datos si solo hay uno o dos formatos que necesita. Esto le ahorrará tiempo en los casos en que los datos del Portapapeles admitan significativamente más formatos que la aplicación.

     O bien

   - Llame a la `BeginEnumFormats` función miembro del objeto de datos para empezar a enumerar los formatos disponibles en el Portapapeles. A `GetNextFormat` continuación, llame hasta que el Portapapeles devuelva un formato que admita la aplicación o no haya más formatos.

Si está utilizando **ON_UPDATE_COMMAND_UI**, ahora puede activar pegar y, posiblemente, pegar elementos especiales en el menú Editar. Para ello, llame `CMenu::EnableMenuItem` `CCmdUI::Enable`a cualquiera o . Para obtener más información sobre lo que deben hacer las aplicaciones contenedoras con los elementos de menú y cuándo, vea [Menús y recursos: adiciones](../mfc/menus-and-resources-container-additions.md)de contenedor .

## <a name="retrieving-data-from-a-data-object"></a><a name="_core_retrieving_data_from_a_data_object"></a>Recuperación de datos de un objeto de datos

Una vez que haya decidido un formato de datos, todo lo que queda es recuperar los datos del objeto de datos. Para ello, el usuario decide dónde colocar los datos y la aplicación llama a la función adecuada. Los datos estarán disponibles en uno de los siguientes medios:

|Media|Función para llamar|
|------------|----------------------|
|Memoria global`HGLOBAL`( )|`COleDataObject::GetGlobalData`|
|Archivo`CFile`( )|`COleDataObject::GetFileData`|
|**Estructura STGMEDIUM** (`IStorage`)|`COleDataObject::GetData`|

Normalmente, el medio se especificará junto con su formato de Portapapeles. Por ejemplo, **CF_EMBEDDEDSTRUCT** un objeto CF_EMBEDDEDSTRUCT `IStorage` siempre está en un medio que requiere una estructura **STGMEDIUM.** Por lo tanto, se utiliza `GetData` porque es la única de estas funciones que puede aceptar una estructura **STGMEDIUM.**

Para los casos en los `IStream` `HGLOBAL` que el formato del `CFile` Portapapeles está en un o medio, el marco de trabajo puede proporcionar un puntero que haga referencia a los datos. A continuación, la aplicación puede utilizar la lectura de archivos para obtener los datos de la misma manera que podría importar datos de un archivo. Esencialmente, esta es la interfaz `OnRenderData` `OnRenderFileData` del lado cliente a las rutinas y en el origen de datos.

El usuario ahora puede insertar datos en el documento al igual que para cualquier otro dato en el mismo formato.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué quieres saber más sobre

- [Arrastrar y soltar](../mfc/drag-and-drop-ole.md)

- [Portapapeles](../mfc/clipboard.md)

## <a name="see-also"></a>Consulte también

[Objetos de datos y orígenes de datos (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[COleDataObject (clase)](../mfc/reference/coledataobject-class.md)<br/>
[COleDataSource (clase)](../mfc/reference/coledatasource-class.md)
