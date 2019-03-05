---
title: 'Objetos de datos y orígenes de datos: Manipulación'
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
ms.openlocfilehash: 81dfe911866c4d1ba1720ee2c9854076c499f0a3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57286756"
---
# <a name="data-objects-and-data-sources-manipulation"></a>Objetos de datos y orígenes de datos: Manipulación

Después de crear un objeto de datos o un origen de datos, puede realizar un número de operaciones comunes en los datos, como insertar y quitar datos, enumerar los formatos de que los datos están en y mucho más. En este artículo se describe las técnicas necesarias para completar las operaciones más habituales. Entre los temas se incluyen los siguientes:

- [Insertar datos en un origen de datos](#_core_inserting_data_into_a_data_source)

- [Determinar los formatos disponibles en un objeto de datos](#_core_determining_the_formats_available_in_a_data_object)

- [Recuperación de datos de un objeto de datos](#_core_retrieving_data_from_a_data_object)

##  <a name="_core_inserting_data_into_a_data_source"></a> Insertar datos en un origen de datos

Cómo se insertan datos en un origen de datos depende de si los datos se proporcionan inmediatamente o a petición y en qué medio se proporcionan. Las posibilidades son como sigue.

### <a name="supplying-data-immediately-immediate-rendering"></a>Suministrar datos inmediatamente (procesamiento inmediato)

- Llamar a `COleDataSource::CacheGlobalData` repetidamente para cada formato de Portapapeles en el que está proporcionando los datos. Pase el formato del Portapapeles para su uso, un identificador de la memoria que contiene los datos y, opcionalmente, un **FORMATETC** estructura que describe los datos.

     O bien

- Si desea trabajar directamente con **STGMEDIUM** estructuras, se llama a `COleDataSource::CacheData` en lugar de `COleDataSource::CacheGlobalData` en la opción anterior.

### <a name="supplying-data-on-demand-delayed-rendering"></a>Suministrar datos a petición (representación retrasada)

Se trata de un tema avanzado.

- Llamar a `COleDataSource::DelayRenderData` repetidamente para cada formato de Portapapeles en el que está proporcionando los datos. Pase el formato del Portapapeles que se usará y, opcionalmente, un **FORMATETC** estructura que describe los datos. Cuando se solicitan los datos, el marco llamará `COleDataSource::OnRenderData`, que debe reemplazar.

     O bien

- Si usa un `CFile` objeto para proporcionar los datos, llame a `COleDataSource::DelayRenderFileData` en lugar de `COleDataSource::DelayRenderData` en la opción anterior. Cuando se solicitan los datos, el marco llamará `COleDataSource::OnRenderFileData`, que debe reemplazar.

##  <a name="_core_determining_the_formats_available_in_a_data_object"></a> Determinar los formatos disponibles en un objeto de datos

Antes de que una aplicación permite al usuario pegar datos en ella, debe saber si hay formatos que puede controlar en el Portapapeles. Para ello, la aplicación debe hacer lo siguiente:

1. Crear un `COleDataObject` objeto y un **FORMATETC** estructura.

1. Llamar al objeto de datos `AttachClipboard` función miembro para asociar el objeto de datos con los datos en el Portapapeles.

1. Realice una de las siguientes acciones:

   - Llamar al objeto de datos `IsDataAvailable` necesita la función de miembro, si hay solo uno o dos formatos. Esto le permitirá ahorrar tiempo en casos donde los datos en el Portapapeles admiten muchos más formatos que la aplicación.

         -or-

   - Llamar al objeto de datos `BeginEnumFormats` función miembro empiecen a enumerar los formatos disponibles en el Portapapeles. A continuación, llame a `GetNextFormat` hasta que el Portapapeles devuelve un formato de la aplicación admite o no hay ningún formato más.

Si usas **ON_UPDATE_COMMAND_UI**, ahora puede habilitar el pegado y, posiblemente, los elementos de pegado especial en el menú Edición. Para ello, llame al `CMenu::EnableMenuItem` o `CCmdUI::Enable`. Para obtener más información acerca de qué contenedor las aplicaciones deben hacer con los elementos de menú y cuándo, vea [menús y recursos: Adiciones de contenedor](../mfc/menus-and-resources-container-additions.md).

##  <a name="_core_retrieving_data_from_a_data_object"></a> Recuperación de datos de un objeto de datos

Una vez que haya decidido el formato de datos, todo lo que queda es recuperar los datos del objeto de datos. Para ello, el usuario decide dónde colocar los datos y la aplicación llama a la función adecuada. Los datos estarán disponibles en uno de los siguientes medios:

|Medium|Función para llamar a|
|------------|----------------------|
|Memoria global (`HGLOBAL`)|`COleDataObject::GetGlobalData`|
|Archivo (`CFile`)|`COleDataObject::GetFileData`|
|**STGMEDIUM** estructura (`IStorage`)|`COleDataObject::GetData`|

Normalmente, se especificará el medio junto con su formato de Portapapeles. Por ejemplo, un **CF_EMBEDDEDSTRUCT** objeto siempre está en un `IStorage` medio que requiere un **STGMEDIUM** estructura. Por lo tanto, se usaría `GetData` porque es la única de estas funciones que puede aceptar un **STGMEDIUM** estructura.

Para los casos donde es el formato del Portapapeles en una `IStream` o `HGLOBAL` medio, el marco de trabajo puede proporcionar un `CFile` puntero que hace referencia a los datos. La aplicación, a continuación, puede usar para obtener los datos de gran parte del mismo modo que podría importar datos desde un archivo de lectura de archivos. En esencia, esta es la interfaz de cliente para el `OnRenderData` y `OnRenderFileData` rutinas del origen de datos.

El usuario puede ahora insertar datos en el documento lo haría con cualquier otro dato con el mismo formato.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Arrastrar y colocar](../mfc/drag-and-drop-ole.md)

- [Portapapeles](../mfc/clipboard.md)

## <a name="see-also"></a>Vea también

[Objetos de datos y orígenes de datos (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[COleDataObject (clase)](../mfc/reference/coledataobject-class.md)<br/>
[COleDataSource (clase)](../mfc/reference/coledatasource-class.md)
