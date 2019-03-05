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
ms.openlocfilehash: 8ae701af3dbf45a1b48ef223f421d17f6abee213
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326633"
---
# <a name="containers-compound-files"></a>Contenedores: Archivos compuestos

En este artículo se explica los componentes y la implementación de archivos compuestos y las ventajas y desventajas de usar archivos compuestos en las aplicaciones OLE.

Archivos compuestos son una parte integral de OLE. Se utilizan para facilitar la transferencia de datos y almacenamiento de documentos OLE. Archivos compuestos son una implementación del modelo de almacenamiento estructurado activo. Interfaces coherentes existen que admiten la serialización para un almacenamiento, una secuencia o un objeto de archivo. Las clases admiten archivos compuestos en la biblioteca Microsoft Foundation Class `COleStreamFile` y `COleDocument`.

> [!NOTE]
>  Uso de un archivo compuesto no implica que la información procede de un documento compuesto o de un documento OLE. Archivos compuestos son simplemente una de las formas de almacenar documentos compuestos, documentos OLE y otros datos.

##  <a name="_core_components_of_a_compound_file"></a> Componentes de un archivo compuesto

La implementación de OLE de archivos compuestos utiliza tres tipos de objetos: objetos de secuencia, los objetos de almacenamiento, y `ILockBytes` objetos. Estos objetos son similares a los componentes de un sistema de archivos estándar de las maneras siguientes:

- Objetos Stream, como los archivos, almacenan de datos de cualquier tipo.

- Objetos de almacenamiento, como los directorios, pueden contener otros objetos de almacenamiento y la secuencia.

- `LockBytes` los objetos representan la interfaz entre los objetos de almacenamiento y el hardware físico. Determinan cómo se escriben los bytes reales a cualquier dispositivo de almacenamiento la `LockBytes` tiene acceso objetos, como una unidad de disco duro o un área de memoria global. Para obtener más información acerca de `LockBytes` objetos y el `ILockBytes` interfaz, vea el *referencia del programador OLE*.

##  <a name="_core_advantages_and_disadvantages_of_compound_files"></a> Ventajas y desventajas de los archivos compuestos

Archivos compuestos proporcionan beneficios no están disponibles en los métodos anteriores de almacenamiento de archivos. Son los siguientes:

- Acceso a archivo incremental.

- Modos de acceso de archivo.

- Estandarización de estructura de archivos.

Los posibles inconvenientes de los archivos compuestos: problemas de rendimiento y tamaño grandes relativas al almacenamiento en discos, debe ser considerada cuando decida si se usan en la aplicación.

###  <a name="_core_incremental_access_to_files"></a> Acceso incremental a archivos

Acceso incremental a archivos es una ventaja de usar archivos compuestos automática. Dado que un archivo compuesto puede verse como un "sistema de archivos dentro de un archivo", los tipos de objetos individuales, como secuencia o de almacenamiento, pueden tener acceso sin necesidad de cargar el archivo completo. Esto puede reducir drásticamente el tiempo que una aplicación necesita acceder a los nuevos objetos para editar el usuario. Actualización incremental, basada en el mismo concepto, ofrece ventajas similares. En lugar de guardar todo el archivo para guardar los cambios realizados en un objeto, OLE guarda sólo el objeto stream o almacenamiento editado por el usuario.

###  <a name="_core_file_access_modes"></a> Modos de acceso de archivo

Ser capaz de determinar cuándo se confirman en el disco los cambios efectuados en un archivo compuesto es otra ventaja de usar archivos compuestos. El modo en que se accede a los archivos con transacciones o directa, determina cuando se confirman los cambios.

- Modo de transacción utiliza una operación de confirmación en dos fases para realizar cambios en objetos en un archivo compuesto, con lo que mantendrá la antigua y las nuevas copias del documento disponible hasta que el usuario decide guardar o deshacer los cambios.

- Modo directo incorpora los cambios realizados en el documento cuando se realizan, sin la capacidad de deshacer más adelante.

Para obtener más información acerca de los modos de acceso, consulte el *referencia del programador OLE*.

###  <a name="_core_standardization"></a> Estandarización

La estructura estandarizada de los archivos compuestos permite que distintas aplicaciones OLE examinar los archivos compuestos, creados por la aplicación OLE sin el conocimiento de la aplicación que se creó el archivo.

###  <a name="_core_size_and_performance_considerations"></a> Consideraciones de rendimiento y tamaño

Dada la complejidad de la estructura de almacenamiento de archivo compuesto y la capacidad de guardar los datos de forma incremental, con este formato de archivos tienden a ser mayor que otros archivos de uso no estructurado o almacenamiento de "archivo sin formato". Si la aplicación con frecuencia se carga y guarda los archivos, el uso de archivos compuestos puede provocar mucho más rápidamente que los archivos de aumentar el tamaño del archivo. Dado que los archivos compuestos pueden obtener grandes, el tiempo de acceso para archivos almacenados en y se carga desde los disquetes también puede verse afectado, lo que provocará un acceso más lento a los archivos.

Otro problema que afecta al rendimiento es la fragmentación de archivo compuesto. El tamaño de un archivo compuesto viene determinada por la diferencia entre los sectores de disco primero y último usa el archivo. Un archivo fragmentado puede contener muchas áreas de espacio libre que no contienen datos, pero se cuentan al calcular el tamaño. Durante la vigencia de un archivo compuesto, estas áreas se crean mediante la inserción o eliminación de objetos de almacenamiento.

##  <a name="_core_using_compound_files_format_for_your_data"></a> Utiliza el formato de archivos compuestos para los datos

Después de crear correctamente una aplicación que tiene una clase de documento que se deriva de `COleDocument`, asegúrese de que el constructor del documento principal llama a `EnableCompoundFile`. Cuando el Asistente para aplicaciones crea aplicaciones de contenedor OLE, se inserta esta llamada.

En el *referencia del programador OLE*, consulte [IStream](/windows/desktop/api/objidl/nn-objidl-istream), [IStorage](/windows/desktop/api/objidl/nn-objidl-istorage), y [ILockBytes](/windows/desktop/api/objidl/nn-objidl-ilockbytes).

## <a name="see-also"></a>Vea también

[Contenedores](../mfc/containers.md)<br/>
[Contenedores: Problemas de la interfaz de usuario](../mfc/containers-user-interface-issues.md)<br/>
[COleStreamFile (clase)](../mfc/reference/colestreamfile-class.md)<br/>
[COleDocument (clase)](../mfc/reference/coledocument-class.md)
