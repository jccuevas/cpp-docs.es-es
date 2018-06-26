---
title: 'Objetos de datos y orígenes de datos: manipulación | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f276e85be33f3042b19ab7dc6158a4e9f856fb2e
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929866"
---
# <a name="data-objects-and-data-sources-manipulation"></a>Objetos de datos y orígenes de datos: manipulación
Una vez creado un objeto de datos o un origen de datos, puede realizar una serie de operaciones comunes en los datos, como insertar y eliminar datos, enumerar los formatos de que los datos están en y mucho más. Este artículo describen las técnicas necesarias para completar las operaciones más habituales. Entre los temas se incluyen los siguientes:  
  
-   [Insertar datos en un origen de datos](#_core_inserting_data_into_a_data_source)  
  
-   [Determinar los formatos disponibles en un objeto de datos](#_core_determining_the_formats_available_in_a_data_object)  
  
-   [Recuperación de datos de un objeto de datos](#_core_retrieving_data_from_a_data_object)  
  
##  <a name="_core_inserting_data_into_a_data_source"></a> Insertar datos en un origen de datos  
 ¿Cómo se insertan los datos en un origen de datos depende de si los datos se suministran inmediatamente o a petición y medio en que se proporciona. Las posibilidades son como se indica a continuación.  
  
### <a name="supplying-data-immediately-immediate-rendering"></a>Suministrar datos inmediatamente (procesamiento inmediato)  
  
-   Llame a `COleDataSource::CacheGlobalData` repetidamente para cada formato de Portapapeles en el que está proporcionando los datos. Pase el formato de Portapapeles para usarse, un identificador de la memoria que contiene los datos y, opcionalmente, un **FORMATETC** estructura que describa los datos.  
  
     O bien  
  
-   Si desea trabajar directamente con **STGMEDIUM** estructuras, se llama a `COleDataSource::CacheData` en lugar de `COleDataSource::CacheGlobalData` en la opción anterior.  
  
### <a name="supplying-data-on-demand-delayed-rendering"></a>Proporciona datos a petición (procesamiento aplazado)  
 Se trata de un tema avanzado.  
  
-   Llame a `COleDataSource::DelayRenderData` repetidamente para cada formato de Portapapeles en el que está proporcionando los datos. Pase el formato de Portapapeles para usarse y, opcionalmente, un **FORMATETC** estructura que describa los datos. Cuando se solicitan los datos, el marco llamará `COleDataSource::OnRenderData`, que es necesario reemplazar.  
  
     O bien  
  
-   Si utiliza un `CFile` objeto que se va a proporcionar los datos, llame a `COleDataSource::DelayRenderFileData` en lugar de `COleDataSource::DelayRenderData` en la opción anterior. Cuando se solicitan los datos, el marco llamará `COleDataSource::OnRenderFileData`, que es necesario reemplazar.  
  
##  <a name="_core_determining_the_formats_available_in_a_data_object"></a> Determinar los formatos disponibles en un objeto de datos  
 Antes de que una aplicación permite al usuario pegar datos en él, debe saber si hay formatos que puede controlar en el Portapapeles. Para ello, la aplicación debe hacer lo siguiente:  
  
1.  Crear un `COleDataObject` objeto y un **FORMATETC** estructura.  
  
2.  Llamar al objeto de datos `AttachClipboard` función de miembro para asociar el objeto de datos con los datos en el Portapapeles.  
  
3.  Realice una de las siguientes acciones:  
  
    -   Llamar al objeto de datos `IsDataAvailable` necesario la función de miembro si hay solo uno o dos formatos. Esto le permitirá ahorrar tiempo en casos donde los datos en el Portapapeles es compatible con muchos más formatos que la aplicación.  
  
         O bien  
  
    -   Llamar al objeto de datos `BeginEnumFormats` función de miembro para empezar a enumerar los formatos disponibles en el Portapapeles. A continuación, llame a `GetNextFormat` hasta que el Portapapeles devuelva un formato de la aplicación admite o no hay ningún formato más.  
  
 Si utilizas **ON_UPDATE_COMMAND_UI**, ahora puede habilitar la pegar y, posiblemente, elementos de pegado especial en el menú Edición. Para ello, llame a `CMenu::EnableMenuItem` o `CCmdUI::Enable`. Para obtener más información acerca de qué contenedor deben hacer con los elementos de menú y, vea aplicaciones [menús y recursos: adiciones de contenedor](../mfc/menus-and-resources-container-additions.md).  
  
##  <a name="_core_retrieving_data_from_a_data_object"></a> Recuperación de datos de un objeto de datos  
 Una vez que haya decidido en un formato de datos, lo único que queda es recuperar los datos del objeto de datos. Para ello, el usuario decide dónde colocar los datos y la aplicación llama a la función adecuada. Los datos estarán disponibles en uno de los siguientes medios:  
  
|Medium|Función que se llama|  
|------------|----------------------|  
|Memoria global (`HGLOBAL`)|`COleDataObject::GetGlobalData`|  
|Archivo (`CFile`)|`COleDataObject::GetFileData`|  
|**STGMEDIUM** estructura (`IStorage`)|`COleDataObject::GetData`|  
  
 Normalmente, se especificará el medio junto con su formato de Portapapeles. Por ejemplo, un **CF_EMBEDDEDSTRUCT** objeto siempre está en un `IStorage` medio que requiere un **STGMEDIUM** estructura. Por lo tanto, usaría `GetData` porque es la única de estas funciones que puede aceptar un **STGMEDIUM** estructura.  
  
 Para los casos donde es el formato del Portapapeles en una `IStream` o `HGLOBAL` intermedio, el marco de trabajo puede proporcionar un `CFile` puntero que hace referencia a los datos. La aplicación, a continuación, puede utilizar para obtener los datos en gran parte de la misma manera que podría importar datos desde un archivo de lectura de archivos. Básicamente, se trata de la interfaz de cliente para la `OnRenderData` y `OnRenderFileData` rutinas en el origen de datos.  
  
 El usuario puede ahora insertar datos en el documento al igual que para cualquier otro dato en el mismo formato.  
  
### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Arrastrar y colocar](../mfc/drag-and-drop-ole.md)  
  
-   [Portapapeles](../mfc/clipboard.md)  
  
## <a name="see-also"></a>Vea también  
 [Objetos de datos y orígenes de datos (OLE)](../mfc/data-objects-and-data-sources-ole.md)   
 [Clase COleDataObject](../mfc/reference/coledataobject-class.md)   
 [COleDataSource (clase)](../mfc/reference/coledatasource-class.md)
