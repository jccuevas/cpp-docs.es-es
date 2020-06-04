---
title: 'Contenedores: Archivos compuestos'
ms.date: 11/04/2016
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
ms.openlocfilehash: 98166a355fd267ecbec0a7f0cc1d18fd0b2e7cd0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353587"
---
# <a name="containers-compound-files"></a>Contenedores: Archivos compuestos

En este artículo se explican los componentes y la implementación de archivos compuestos y las ventajas y desventajas del uso de archivos compuestos en las aplicaciones OLE.

Los archivos compuestos son una parte integral de OLE. Se utilizan para facilitar la transferencia de datos y el almacenamiento de documentos OLE. Los archivos compuestos son una implementación del modelo de almacenamiento estructurado activo. Existen interfaces coherentes que admiten la serialización en un almacenamiento, una secuencia o un objeto de archivo. Las clases y los archivos compuestos `COleStreamFile` `COleDocument`son compatibles con la biblioteca Microsoft Foundation Class en las clases y .

> [!NOTE]
> El uso de un archivo compuesto no implica que la información provenga de un documento OLE o un documento compuesto. Los archivos compuestos son solo una de las formas de almacenar documentos compuestos, documentos OLE y otros datos.

## <a name="components-of-a-compound-file"></a><a name="_core_components_of_a_compound_file"></a>Componentes de un archivo compuesto

La implementación OLE de archivos compuestos utiliza tres `ILockBytes` tipos de objetos: objetos de secuencia, objetos de almacenamiento y objetos. Estos objetos son similares a los componentes de un sistema de archivos estándar de las siguientes maneras:

- Los objetos de transmisión, como los archivos, almacenan datos de cualquier tipo.

- Los objetos de almacenamiento, como los directorios, pueden contener otros objetos de almacenamiento y secuencia.

- `LockBytes`objetos representan la interfaz entre los objetos de almacenamiento y el hardware físico. Determinan cómo se escriben los bytes `LockBytes` reales en cualquier dispositivo de almacenamiento al que acceda el objeto, como un disco duro o un área de memoria global. Para obtener `LockBytes` más información `ILockBytes` acerca de los objetos y la interfaz, vea la *referencia del programador OLE*.

## <a name="advantages-and-disadvantages-of-compound-files"></a><a name="_core_advantages_and_disadvantages_of_compound_files"></a>Ventajas y desventajas de los archivos compuestos

Los archivos compuestos proporcionan ventajas que no están disponibles con métodos anteriores de almacenamiento de archivos. Incluyen:

- Acceso incremental a archivos.

- Modos de acceso a archivos.

- Estandarización de la estructura de archivos.

Las posibles desventajas de los archivos compuestos (problemas de gran tamaño y rendimiento relacionados con el almacenamiento en discos de disquete) deben tenerse en cuenta al decidir si utilizarlos en la aplicación.

### <a name="incremental-access-to-files"></a><a name="_core_incremental_access_to_files"></a>Acceso incremental a archivos

El acceso incremental a los archivos es una ventaja automática del uso de archivos compuestos. Dado que un archivo compuesto se puede ver como un "sistema de archivos dentro de un archivo", se puede acceder a tipos de objetos individuales, como la secuencia o el almacenamiento, sin necesidad de cargar todo el archivo. Esto puede reducir drásticamente el tiempo que una aplicación necesita tener acceso a nuevos objetos para su edición por el usuario. La actualización incremental, basada en el mismo concepto, ofrece ventajas similares. En lugar de guardar todo el archivo solo para guardar los cambios realizados en un objeto, OLE guarda solo la secuencia o el objeto de almacenamiento editado por el usuario.

### <a name="file-access-modes"></a><a name="_core_file_access_modes"></a>Modos de acceso a archivos

Ser capaz de determinar cuándo los cambios en los objetos de un archivo compuesto se confirman en el disco es otra ventaja de usar archivos compuestos. El modo en el que se tiene acceso a los archivos, ya sea transaccionalo o directo, determina cuándo se confirman los cambios.

- El modo de transacciones usa una operación de confirmación de dos fases para realizar cambios en los objetos de un archivo compuesto, manteniendo así las copias antiguas y nuevas del documento disponibles hasta que el usuario elija guardar o deshacer los cambios.

- El modo directo incorpora cambios en el documento a medida que se realizan, sin la capacidad de deshacerlos posteriormente.

Para obtener más información acerca de los modos de acceso, vea la *referencia del programador OLE*.

### <a name="standardization"></a><a name="_core_standardization"></a>Normalización

La estructura estandarizada de archivos compuestos permite que diferentes aplicaciones OLE exploren los archivos compuestos creados por la aplicación OLE sin conocimiento de la aplicación que realmente creó el archivo.

### <a name="size-and-performance-considerations"></a><a name="_core_size_and_performance_considerations"></a>Consideraciones sobre el tamaño y el rendimiento

Debido a la complejidad de la estructura de almacenamiento de archivos compuesta y la capacidad de guardar datos de forma incremental, los archivos que utilizan este formato tienden a ser más grandes que otros archivos que utilizan almacenamiento no estructurado o "archivo plano". Si la aplicación carga y guarda archivos con frecuencia, el uso de archivos compuestos puede hacer que el tamaño del archivo aumente mucho más rápidamente que los archivos no compuestos. Debido a que los archivos compuestos pueden hacerse grandes, el tiempo de acceso para los archivos almacenados y cargados desde disquetes también puede verse afectado, lo que resulta en un acceso más lento a los archivos.

Otro problema que afecta al rendimiento es la fragmentación de archivos compuestos. El tamaño de un archivo compuesto viene determinado por la diferencia entre el primer y el último sector de disco utilizado por el archivo. Un archivo fragmentado puede contener muchas áreas de espacio libre que no contienen datos, pero se cuentan al calcular el tamaño. Durante la duración de un archivo compuesto, estas áreas se crean mediante la inserción o eliminación de objetos de almacenamiento.

## <a name="using-compound-files-format-for-your-data"></a><a name="_core_using_compound_files_format_for_your_data"></a>Uso del formato de archivos compuestos para sus datos

Después de crear correctamente una aplicación que `COleDocument`tiene una clase de `EnableCompoundFile`documento derivada de , asegúrese de que el constructor de documento principal llama . Cuando el asistente para aplicaciones crea aplicaciones contenedoras OLE, esta llamada se inserta automáticamente.

En la *referencia del programador OLE*, vea [IStream](/windows/win32/api/objidl/nn-objidl-istream), [IStorage](/windows/win32/api/objidl/nn-objidl-istorage)e [ILockBytes](/windows/win32/api/objidl/nn-objidl-ilockbytes).

## <a name="see-also"></a>Consulte también

[Contenedores](../mfc/containers.md)<br/>
[Contenedores: Problemas de la interfaz de usuario](../mfc/containers-user-interface-issues.md)<br/>
[COleStreamFile (Clase)](../mfc/reference/colestreamfile-class.md)<br/>
[COleDocument (Clase)](../mfc/reference/coledocument-class.md)
