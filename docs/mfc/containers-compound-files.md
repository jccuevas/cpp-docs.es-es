---
title: 'Contenedores: Archivos compuestos | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- compound files [MFC]
- compound documents
- containers [MFC], compound files
- OLE documents [MFC], compound files
- performance [MFC], compound files
- files [MFC], compound
- standardized file structure compound files
- documents [MFC], compound
- documents [MFC], OLE
- OLE containers [MFC], compound files
- access modes for files [MFC]
ms.assetid: 8b83cb3e-76c8-4bbe-ba16-737092b36f49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8983fd8cb51a9f305ef4b0fad4d546fc8091f5a5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348350"
---
# <a name="containers-compound-files"></a>Contenedores: Archivos compuestos
En este artículo se explica los componentes y la implementación de archivos compuestos así como las ventajas y desventajas del uso de archivos compuestos en las aplicaciones OLE.  
  
 Archivos compuestos son una parte integral de OLE. Se utilizan para facilitar la transferencia de datos y almacenamiento de documentos OLE. Archivos compuestos son una implementación del modelo de almacenamiento estructurado activo. Interfaces coherentes existen que admiten la serialización en un almacenamiento, una secuencia o un objeto de archivo. Se admiten archivos compuestos en la biblioteca Microsoft Foundation Class por las clases de `COleStreamFile` y `COleDocument`.  
  
> [!NOTE]
>  Uso de un archivo compuesto no implica que la información provenga de un documento OLE o un documento compuesto. Archivos compuestos son una de las formas de almacenar documentos compuestos, documentos OLE y otros datos.  
  
##  <a name="_core_components_of_a_compound_file"></a> Componentes de un archivo compuesto  
 La implementación OLE de los archivos compuestos utiliza tres tipos de objetos: objetos de secuencia, objetos de almacenamiento, y `ILockBytes` objetos. Estos objetos son similares a los componentes de un sistema de archivos estándar de las maneras siguientes:  
  
-   Objetos de secuencia, como los archivos, almacenan datos de cualquier tipo.  
  
-   Objetos de almacenamiento, como los directorios, pueden contener otros objetos de almacenamiento y el flujo.  
  
-   **LockBytes** objetos representan la interfaz entre los objetos de almacenamiento y el hardware físico. Determinan cómo se escriben los bytes reales para cualquier dispositivo de almacenamiento del **LockBytes** obtiene acceso objetos, como una unidad de disco duro o un área de la memoria global. Para obtener más información acerca de **LockBytes** objetos y `ILockBytes` de la interfaz, vea la *referencia del programador de OLE*.  
  
##  <a name="_core_advantages_and_disadvantages_of_compound_files"></a> Ventajas y desventajas de los archivos compuestos  
 Archivos compuestos proporcionan ventajas no está disponible en los métodos anteriores de almacenamiento de archivos. Son los siguientes:  
  
-   Acceso a archivo incremental.  
  
-   Modos de acceso de archivo.  
  
-   Normalización de la estructura de archivos.  
  
 Los posibles inconvenientes de los archivos compuestos: problemas importantes de tamaño y de rendimiento relacionados con el almacenamiento en disquetes: debe ser considerada cuando decida si desea utilizarlos en la aplicación.  
  
###  <a name="_core_incremental_access_to_files"></a> Acceso incremental a archivos  
 Acceso incremental a archivos es una ventaja automática del uso de archivos compuestos. Porque un archivo compuesto puede verse como un "sistema de archivos dentro de un archivo", pueden tener acceso a tipos de objeto individuales, por ejemplo, la secuencia o de almacenamiento, sin necesidad de cargar todo el archivo. Esto puede reducir drásticamente el tiempo que una aplicación necesita tener acceso a los nuevos objetos para ser modificado por el usuario. Actualización incremental, basada en el mismo concepto, ofrece ventajas similares. En lugar de guardar todo el archivo para guardar los cambios realizados en un objeto, OLE sólo guarda el flujo o almacenamiento objeto editado por el usuario.  
  
###  <a name="_core_file_access_modes"></a> Modos de acceso de archivo  
 Ser capaz de determinar cuándo se confirman en el disco cambios en los objetos en un archivo compuesto es otra ventaja de utilizar archivos compuestos. El modo en el que se obtiene acceso a archivos, transacciones o directa, determina cuando se confirman los cambios.  
  
-   Modo de transacción utiliza una operación de confirmación en dos fases para realizar cambios en objetos en un archivo compuesto, manteniendo la antigua y las nuevas copias del documento disponible hasta que el usuario decide guardar o deshacer los cambios.  
  
-   Modo directo incorpora los cambios realizados en el documento según se realizan, sin la capacidad para deshacerlos más tarde.  
  
 Para obtener más información acerca de los modos de acceso, consulte el *referencia del programador de OLE*.  
  
###  <a name="_core_standardization"></a> Estandarización  
 La estructura estandarizada de los archivos compuestos permite que distintas aplicaciones OLE exploren archivos compuestos creados por la aplicación OLE con ningún conocimiento de la aplicación que se creó el archivo.  
  
###  <a name="_core_size_and_performance_considerations"></a> Consideraciones de rendimiento y tamaño  
 Dada la complejidad de la estructura de almacenamiento de archivo compuesto y la capacidad de guardar los datos de forma incremental, archivos con este formato tienden a ser mayor que otros archivos de uso no estructurado o almacenamiento de "archivo sin formato". Si la aplicación carga y guarda los archivos con frecuencia, uso de archivos compuestos puede hacer que el tamaño de archivo aumentar mucho más rápidamente que los archivos. Como archivos compuestos pueden llegar grandes, la hora de acceso de archivos almacenados en y cargar desde disquetes también puede verse afectada, lo que produce un acceso más lento a los archivos.  
  
 Otro problema que afecta al rendimiento es la fragmentación de archivo compuesto. El tamaño de un archivo compuesto se determina por la diferencia entre los sectores de disco primero y último usa el archivo. Un archivo fragmentado puede contener muchas áreas de espacio libre que no contienen datos, pero se cuentan al calcular el tamaño. Durante la duración de un archivo compuesto, estas áreas se crean mediante la inserción o eliminación de objetos de almacenamiento.  
  
##  <a name="_core_using_compound_files_format_for_your_data"></a> Con el formato de archivos compuestos para los datos  
 Después de crear correctamente una aplicación que tiene una clase de documento derivada de `COleDocument`, asegúrese de que el constructor del documento principal llama a `EnableCompoundFile`. Cuando el Asistente para aplicaciones crea aplicaciones de contenedor OLE, esta llamada se inserta automáticamente.  
  
 En el *referencia del programador de OLE*, consulte [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034), [IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015), y [ILockBytes](http://msdn.microsoft.com/library/windows/desktop/aa379238).  
  
## <a name="see-also"></a>Vea también  
 [Contenedores](../mfc/containers.md)   
 [Contenedores: Problemas de la interfaz de usuario](../mfc/containers-user-interface-issues.md)   
 [Clase COleStreamFile](../mfc/reference/colestreamfile-class.md)   
 [COleDocument (clase)](../mfc/reference/coledocument-class.md)
