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
ms.openlocfilehash: f1a83511edbf240d9a05d6d489f6cda9453ccea9
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620401"
---
# <a name="data-objects-and-data-sources-manipulation"></a>Objetos de datos y orígenes de datos: manipulación

Una vez creado un objeto de datos o un origen de datos, puede realizar una serie de operaciones comunes en los datos, como insertar y quitar datos, enumerar los formatos en los que están los datos, etc. En este artículo se describen las técnicas necesarias para completar las operaciones más comunes. Contenido de los temas:

- [Insertar datos en un origen de datos](#_core_inserting_data_into_a_data_source)

- [Determinar los formatos disponibles en un objeto de datos](#_core_determining_the_formats_available_in_a_data_object)

- [Recuperar datos de un objeto de datos](#_core_retrieving_data_from_a_data_object)

## <a name="inserting-data-into-a-data-source"></a><a name="_core_inserting_data_into_a_data_source"></a>Insertar datos en un origen de datos

La forma en que los datos se insertan en un origen de datos depende de si los datos se proporcionan inmediatamente o a petición, y en qué medio se proporciona. Las posibilidades son las siguientes:

### <a name="supplying-data-immediately-immediate-rendering"></a>Proporcionar datos inmediatamente (representación inmediata)

- Llame a `COleDataSource::CacheGlobalData` repetidamente para cada formato del portapapeles en el que va a proporcionar datos. Pase el formato del portapapeles que se va a usar, un identificador de la memoria que contiene los datos y, opcionalmente, una estructura **FORMATETC** que describe los datos.

     o bien

- Si desea trabajar directamente con estructuras **STGMEDIUM** , llame a `COleDataSource::CacheData` en lugar de `COleDataSource::CacheGlobalData` en la opción anterior.

### <a name="supplying-data-on-demand-delayed-rendering"></a>Proporcionar datos a petición (representación retrasada)

Este es un tema avanzado.

- Llame a `COleDataSource::DelayRenderData` repetidamente para cada formato del portapapeles en el que va a proporcionar datos. Pase el formato del portapapeles que se va a usar y, opcionalmente, una estructura **FORMATETC** que describa los datos. Cuando se solicitan los datos, el marco de trabajo llamará a `COleDataSource::OnRenderData` , que debe reemplazar.

     o bien

- Si usa un `CFile` objeto para proporcionar los datos, llame a `COleDataSource::DelayRenderFileData` en lugar de `COleDataSource::DelayRenderData` en la opción anterior. Cuando se solicitan los datos, el marco de trabajo llamará a `COleDataSource::OnRenderFileData` , que debe reemplazar.

## <a name="determining-the-formats-available-in-a-data-object"></a><a name="_core_determining_the_formats_available_in_a_data_object"></a>Determinar los formatos disponibles en un objeto de datos

Antes de que una aplicación permita al usuario pegar datos en ella, debe saber si hay formatos en el portapapeles que pueda controlar. Para ello, la aplicación debe hacer lo siguiente:

1. Cree un `COleDataObject` objeto y una estructura **FORMATETC** .

1. Llame a la función miembro del objeto de datos `AttachClipboard` para asociar el objeto de datos a los datos del portapapeles.

1. Lleve a cabo una de las siguientes acciones:

   - Llame a la función miembro del objeto de datos `IsDataAvailable` si solo hay uno o dos formatos necesarios. Esto le ahorrará tiempo en los casos en los que los datos del portapapeles admitan muchos más formatos que la aplicación.

     O bien

   - Llame a la función miembro del objeto de datos `BeginEnumFormats` para empezar a enumerar los formatos disponibles en el portapapeles. Después, llame a `GetNextFormat` hasta que el portapapeles devuelva un formato que admita la aplicación o no haya más formatos.

Si usa **ON_UPDATE_COMMAND_UI**, ahora puede habilitar pegar y, posiblemente, pegar elementos especiales en el menú edición. Para ello, llame a `CMenu::EnableMenuItem` o a `CCmdUI::Enable` . Para obtener más información sobre las aplicaciones contenedoras que deben hacer con los elementos de menú y cuándo, vea [menús y recursos: adiciones de contenedor](menus-and-resources-container-additions.md).

## <a name="retrieving-data-from-a-data-object"></a><a name="_core_retrieving_data_from_a_data_object"></a>Recuperar datos de un objeto de datos

Una vez que haya decidido un formato de datos, todo lo que queda es recuperar los datos del objeto de datos. Para ello, el usuario decide dónde colocar los datos y la aplicación llama a la función adecuada. Los datos estarán disponibles en uno de los siguientes medios:

|Mediana|Función a la que se llama|
|------------|----------------------|
|Memoria global ( `HGLOBAL` )|`COleDataObject::GetGlobalData`|
|Archivo ( `CFile` )|`COleDataObject::GetFileData`|
|Estructura **STGMEDIUM** ( `IStorage` )|`COleDataObject::GetData`|

Normalmente, el medio se especificará junto con el formato del portapapeles. Por ejemplo, un objeto de **CF_EMBEDDEDSTRUCT** siempre está en un `IStorage` medio que requiere una estructura **STGMEDIUM** . Por lo tanto, se usaría `GetData` porque es la única de estas funciones que puede aceptar una estructura **STGMEDIUM** .

En los casos en los que el formato del portapapeles se encuentra en un `IStream` `HGLOBAL` medio o, el marco puede proporcionar un `CFile` puntero que haga referencia a los datos. A continuación, la aplicación puede usar la lectura de archivos para obtener los datos de la misma manera que podría importar datos desde un archivo. Esencialmente, esta es la interfaz del lado cliente para las `OnRenderData` `OnRenderFileData` rutinas y en el origen de datos.

Ahora el usuario puede insertar datos en el documento de la misma manera que para cualquier otro dato en el mismo formato.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Arrastrar y colocar](drag-and-drop-ole.md)

- [Portapapeles](clipboard.md)

## <a name="see-also"></a>Consulte también

[Objetos de datos y orígenes de datos (OLE)](data-objects-and-data-sources-ole.md)<br/>
[COleDataObject (clase)](reference/coledataobject-class.md)<br/>
[COleDataSource (clase)](reference/coledatasource-class.md)
