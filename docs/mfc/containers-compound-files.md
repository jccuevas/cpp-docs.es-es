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
ms.openlocfilehash: 344c444602555e2b5c145e58d237586199b9e1ed
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624817"
---
# <a name="containers-compound-files"></a>Contenedores: Archivos compuestos

En este artículo se explican los componentes y la implementación de archivos compuestos y las ventajas y desventajas del uso de archivos compuestos en las aplicaciones OLE.

Los archivos compuestos son una parte integral de OLE. Se usan para facilitar la transferencia de datos y el almacenamiento de documentos OLE. Los archivos compuestos son una implementación del modelo de almacenamiento estructurado activo. Existen interfaces coherentes que admiten la serialización en un almacenamiento, un flujo o un objeto de archivo. Los archivos compuestos se admiten en el biblioteca MFC por las clases `COleStreamFile` y `COleDocument` .

> [!NOTE]
> El uso de un archivo compuesto no implica que la información proceda de un documento OLE o de un documento compuesto. Los archivos compuestos son solo una de las formas de almacenar documentos compuestos, documentos OLE y otros datos.

## <a name="components-of-a-compound-file"></a><a name="_core_components_of_a_compound_file"></a>Componentes de un archivo compuesto

La implementación OLE de archivos compuestos utiliza tres tipos de objetos: objetos de secuencia, objetos de almacenamiento y `ILockBytes` objetos. Estos objetos son similares a los componentes de un sistema de archivos estándar de las maneras siguientes:

- Los objetos de secuencia, como los archivos, almacenan datos de cualquier tipo.

- Los objetos de almacenamiento, como los directorios, pueden contener otros objetos de almacenamiento y de secuencia.

- `LockBytes`los objetos representan la interfaz entre los objetos de almacenamiento y el hardware físico. Determinan cómo se escriben los bytes reales en cualquier dispositivo de almacenamiento al que `LockBytes` tenga acceso el objeto, como una unidad de disco duro o un área de memoria global. Para obtener más información sobre `LockBytes` los objetos y la `ILockBytes` interfaz, vea la *Referencia del programador de OLE*.

## <a name="advantages-and-disadvantages-of-compound-files"></a><a name="_core_advantages_and_disadvantages_of_compound_files"></a>Ventajas y desventajas de los archivos compuestos

Los archivos compuestos proporcionan ventajas que no están disponibles con los métodos anteriores de almacenamiento de archivos. Son los siguientes:

- Acceso incremental de archivos.

- Modos de acceso a archivos.

- Normalización de la estructura de archivos.

Se deben tener en cuenta las posibles desventajas de los archivos compuestos: problemas de gran tamaño y rendimiento relacionados con el almacenamiento en disquetes, a la hora de decidir si usarlos en la aplicación.

### <a name="incremental-access-to-files"></a><a name="_core_incremental_access_to_files"></a>Acceso incremental a archivos

El acceso incremental a los archivos es una ventaja automática del uso de archivos compuestos. Dado que un archivo compuesto se puede ver como un "sistema de archivos dentro de un archivo", se puede tener acceso a tipos de objetos individuales, como Stream o Storage, sin necesidad de cargar todo el archivo. Esto puede reducir drásticamente el tiempo que una aplicación necesita para tener acceso a los objetos nuevos para que los edite el usuario. La actualización incremental, basada en el mismo concepto, ofrece ventajas similares. En lugar de guardar todo el archivo solo para guardar los cambios realizados en un objeto, OLE guarda solo la secuencia o el objeto de almacenamiento editado por el usuario.

### <a name="file-access-modes"></a><a name="_core_file_access_modes"></a>Modos de acceso a archivos

La capacidad de determinar cuándo se confirman los cambios en los objetos de un archivo compuesto se confirma en el disco es otra ventaja de usar archivos compuestos. El modo en el que se obtiene acceso a los archivos, ya sea con transacciones o directamente, determina cuándo se confirman los cambios.

- El modo de transacción utiliza una operación de confirmación en dos fases para realizar cambios en los objetos de un archivo compuesto, lo que mantiene las copias antiguas y nuevas del documento disponibles hasta que el usuario elige guardar o deshacer los cambios.

- El modo directo incorpora cambios en el documento a medida que se realizan, sin la capacidad de deshacerlos más adelante.

Para obtener más información sobre los modos de acceso, vea la *Referencia del programador de OLE*.

### <a name="standardization"></a><a name="_core_standardization"></a>Normalización

La estructura normalizada de archivos compuestos permite que diferentes aplicaciones OLE examinen los archivos compuestos creados por la aplicación OLE sin conocimiento de la aplicación que realmente creó el archivo.

### <a name="size-and-performance-considerations"></a><a name="_core_size_and_performance_considerations"></a>Consideraciones de tamaño y rendimiento

Debido a la complejidad de la estructura de almacenamiento de archivos compuesto y a la capacidad de guardar los datos de forma incremental, los archivos que usan este formato suelen ser más grandes que otros archivos que usan almacenamiento no estructurado o de archivo sin formato. Si la aplicación carga y guarda archivos con frecuencia, el uso de archivos compuestos puede hacer que el tamaño del archivo aumente mucho más rápidamente que los archivos no compuestos. Dado que los archivos compuestos pueden llegar a ser grandes, el tiempo de acceso para los archivos almacenados y cargados desde disquetes también puede verse afectado, lo que da lugar a un acceso más lento a los archivos.

Otro problema que afecta al rendimiento es la fragmentación de archivos compuestos. El tamaño de un archivo compuesto viene determinado por la diferencia entre el primer y el último sector del disco utilizado por el archivo. Un archivo fragmentado puede contener muchas áreas de espacio disponible que no contienen datos, pero se cuentan al calcular el tamaño. Durante la vigencia de un archivo compuesto, estas áreas se crean mediante la inserción o eliminación de objetos de almacenamiento.

## <a name="using-compound-files-format-for-your-data"></a><a name="_core_using_compound_files_format_for_your_data"></a>Usar el formato de archivos compuestos para los datos

Después de crear correctamente una aplicación que tiene una clase de documento derivada de `COleDocument` , asegúrese de que el constructor del documento principal llama a `EnableCompoundFile` . Cuando el Asistente para aplicaciones crea aplicaciones de contenedor OLE, se inserta esta llamada.

En la *Referencia del programador de OLE*, vea [IStream](/windows/win32/api/objidl/nn-objidl-istream), [IStorage](/windows/win32/api/objidl/nn-objidl-istorage)y [ILockBytes](/windows/win32/api/objidl/nn-objidl-ilockbytes).

## <a name="see-also"></a>Consulte también

[Contenedores](containers.md)<br/>
[Contenedores: Problemas de la interfaz de usuario](containers-user-interface-issues.md)<br/>
[Clase COleStreamFile](reference/colestreamfile-class.md)<br/>
[COleDocument (clase)](reference/coledocument-class.md)
