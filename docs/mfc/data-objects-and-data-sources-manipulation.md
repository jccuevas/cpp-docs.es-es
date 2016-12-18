---
title: "Objetos de datos y or&#237;genes de datos: manipulaci&#243;n | Microsoft Docs"
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
  - "Portapapeles [C++], determinar formatos disponibles"
  - "Portapapeles [C++], pasar información de formato"
  - "objetos de datos [C++], manipular"
  - "orígenes de datos [C++], operaciones de datos"
  - "orígenes de datos [C++], determinar formatos disponibles"
  - "orígenes de datos [C++], insertar datos"
  - "representación retrasada [C++]"
  - "OLE [C++], objetos de datos"
  - "OLE [C++], orígenes de datos"
ms.assetid: f7f27e77-bb5d-4131-b819-d71bf929ebaf
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Objetos de datos y or&#237;genes de datos: manipulaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Después de un objeto de datos o un origen de datos se ha creado, puede realizar varias operaciones comunes en los datos, como insertar y los datos que quita, enumerando los formatos datos está en, y más.  En este artículo se describe las técnicas necesarias para completar las operaciones más comunes.  Entre los temas se incluyen los siguientes:  
  
-   [Insertar datos en un origen de datos](#_core_inserting_data_into_a_data_source)  
  
-   [Determinar los formatos disponibles en un objeto de datos](#_core_determining_the_formats_available_in_a_data_object)  
  
-   [Recuperar datos de un objeto de datos](#_core_retrieving_data_from_a_data_object)  
  
##  <a name="_core_inserting_data_into_a_data_source"></a> Insertar datos en un origen de datos  
 Cómo se insertan los datos en un origen de datos depende de si los datos se proporcione inmediatamente o a petición, y en qué medio se proporciona.  Las posibilidades son los siguientes.  
  
### Proporcionar datos inmediatamente \(representación inmediata\)  
  
-   Pida `COleDataSource::CacheGlobalData` repetidamente cada formato del Portapapeles en el que está proporcionando datos.  Pase el formato del Portapapeles que se utilizarán, un identificador a memoria que contiene los datos y, opcionalmente, una estructura de **FORMATETC** describir los datos.  
  
     O bien  
  
-   Si desea trabajar directamente con estructuras de **STGMEDIUM** , se llama a `COleDataSource::CacheData` en lugar de `COleDataSource::CacheGlobalData` en la opción anterior.  
  
### Proporcionar datos a petición \(la generación retrasado\)  
 Éste es un tema avanzado.  
  
-   Pida `COleDataSource::DelayRenderData` repetidamente cada formato del Portapapeles en el que está proporcionando datos.  Pase el formato del Portapapeles que se van a utilizar y, opcionalmente, una estructura de **FORMATETC** que describe los datos.  Cuando se solicita los datos, el marco llamará a `COleDataSource::OnRenderData`, que debe reemplazar.  
  
     O bien  
  
-   Si utiliza un objeto de `CFile` para proporcionar los datos, llame a `COleDataSource::DelayRenderFileData` en lugar de `COleDataSource::DelayRenderData` en la opción anterior.  Cuando se solicita los datos, el marco llamará a `COleDataSource::OnRenderFileData`, que debe reemplazar.  
  
##  <a name="_core_determining_the_formats_available_in_a_data_object"></a> Determinar los formatos disponibles en un objeto de datos  
 Antes de que una aplicación permite al usuario pegar los datos en ella, necesita saber si hay formatos en el portapapeles que puede controlar.  Para ello, la aplicación debe hacer lo siguiente:  
  
1.  Cree un objeto de `COleDataObject` y una estructura de **FORMATETC** .  
  
2.  Llame a la función miembro de `AttachClipboard` de objeto de datos para asociar el objeto de datos con los datos en el portapapeles.  
  
3.  Siga uno de estos procedimientos:  
  
    -   Llame a la función miembro de `IsDataAvailable` del objeto de datos si solo hay una o dos formatos que necesita.  Esto le ahorrará tiempo en caso de que los datos del portapapeles admite significativamente más formatos que la aplicación.  
  
         O bien  
  
    -   Llame a la función miembro de `BeginEnumFormats` de objeto de datos para iniciar la enumeración de los formatos disponibles en el portapapeles.  Llamar a continuación a `GetNextFormat` hasta el portapapeles devuelve un formato que admite la aplicación o no hay formatos.  
  
 Si usa `ON_UPDATE_COMMAND_UI`, ahora puede habilitar los elementos de pegar y, posiblemente, de pegar especial en el menú Edición.  Para ello, llame `CMenu::EnableMenuItem` o `CCmdUI::Enable`.  Para obtener más información sobre lo que deben tener las aplicaciones contenedoras con elementos de menú y cuándo, vea [Menús y recursos: Adiciones de contenedor](../mfc/menus-and-resources-container-additions.md).  
  
##  <a name="_core_retrieving_data_from_a_data_object"></a> Recuperar datos de un objeto de datos  
 Una vez que haya decidido sobre un formato de datos, todo lo que queda es recuperar los datos del objeto de datos.  Para ello, el usuario decide dónde colocar los datos, y la aplicación llama a la función adecuada.  Los datos estarán disponibles en uno de los medios siguientes:  
  
|Medium|Función a|  
|------------|---------------|  
|Memoria global \(`HGLOBAL`\)|`COleDataObject::GetGlobalData`|  
|Archivo \(`CFile`\)|`COleDataObject::GetFileData`|  
|Estructura de**STGMEDIUM** \(`IStorage`\)|`COleDataObject::GetData`|  
  
 Normalmente, el medio se especificado junto con el formato del Portapapeles.  Por ejemplo, un objeto de **CF\_EMBEDDEDSTRUCT** siempre está en un medio de `IStorage` que requiera una estructura de **STGMEDIUM** .  Por consiguiente, debería `GetData` porque es el único de estas funciones que pueden aceptar una estructura de **STGMEDIUM** .  
  
 Para los casos donde es el formato del Portapapeles en un medio de `IStream` o de `HGLOBAL` , el marco puede proporcionar un puntero de `CFile` que haga referencia a los datos.  La aplicación puede utilizar la lectura de archivo para obtener los datos de la misma forma que se puede importar datos de un archivo.  Esencialmente, ésta es la interfaz del lado cliente a las rutinas de `OnRenderData` y de `OnRenderFileData` en el origen de datos.  
  
 El usuario podrá insertar datos en el documento como para cualquier otro dato en el mismo formato.  
  
### ¿Sobre qué desea obtener más información?  
  
-   [Con el método de arrastrar y colocar](../mfc/drag-and-drop-ole.md)  
  
-   [Portapapeles](../mfc/clipboard.md)  
  
## Vea también  
 [Objetos de datos y orígenes de datos \(OLE\)](../mfc/data-objects-and-data-sources-ole.md)   
 [COleDataObject Class](../mfc/reference/coledataobject-class.md)   
 [COleDataSource Class](../mfc/reference/coledatasource-class.md)