---
title: "Contenedores: Archivos compuestos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "modos de acceso para archivos [C++]"
  - "documentos compuestos"
  - "archivos compuestos"
  - "contenedores [C++], archivos compuestos"
  - "documentos [C++], compuesta"
  - "documentos [C++], OLE"
  - "archivos [C++], compuesta"
  - "contenedores OLE, archivos compuestos"
  - "OLE (documentos), archivos compuestos"
  - "rendimiento [C++], archivos compuestos"
  - "archivos compuestos de estructura de archivo estandarizado"
ms.assetid: 8b83cb3e-76c8-4bbe-ba16-737092b36f49
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Contenedores: Archivos compuestos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica los componentes y la implementación de archivos compuestos y las ventajas y las desventajas de utilizar archivos compuestos en aplicaciones OLE.  
  
 Los archivos compuestos son una parte integral de OLE.  Se utilizan para facilitar la transferencia de datos y el almacenamiento de documento OLE.  Los archivos compuestos son una implementación del modelo activo de almacenamiento estructurado.  Las interfaces coherentes existen esa admiten la serialización en un almacenamiento, una secuencia, o un objeto de archivo.  Los archivos compuestos son compatibles en la biblioteca Microsoft Foundation Class por las clases `COleStreamFile` y `COleDocument`.  
  
> [!NOTE]
>  Mediante un archivo compuesto no implica que la información procede de un documento OLE o documento compuesto.  Los archivos compuestos son solo una de las formas de almacenar documentos compuestos, documentos de OLE, y otros datos.  
  
##  <a name="_core_components_of_a_compound_file"></a> Componentes de un archivo compuesto  
 La implementación OLE de archivos compuestos utiliza tres tipos de objeto: objetos de secuencia, objetos de almacenamiento, y objetos de `ILockBytes` .  Estos objetos son similares a los componentes de un sistema de archivos estándar de las maneras siguientes:  
  
-   Objetos de secuencia, como los archivos, datos almacenados de cualquier tipo.  
  
-   Los objetos de almacenamiento, como directorios, pueden contener otro almacén y objetos de secuencia.  
  
-   Los objetos de**LockBytes** representan la interfaz entre los objetos de almacenamiento y el hardware físico.  Determinan a cómo los bytes reales se escriben cualquier dispositivo de almacenamiento el objeto de **LockBytes** obtiene acceso, por ejemplo un disco duro o un área de memoria global.  Para obtener más información sobre los objetos de **LockBytes** y la interfaz de `ILockBytes` , vea *referencia\) del Programador*.  
  
##  <a name="_core_advantages_and_disadvantages_of_compound_files"></a> Ventajas y Desventajas de archivos compuestos  
 Archivos compuestos proporcionan ventajas no disponibles con métodos anteriores de almacenamiento de archivo.  Son los siguientes:  
  
-   Acceso incremental del archivo.  
  
-   Modos de acceso a archivos.  
  
-   Normalización de la estructura de archivos.  
  
 Las desventajas de posibles archivos compuestos — de gran tamaño y los problemas de rendimiento relacionados con almacenamiento en los discos blandos — deben tenerse en cuenta al decidir si utilizarlos en la aplicación.  
  
###  <a name="_core_incremental_access_to_files"></a> Access incremental a archivos  
 El acceso incremental a archivos es un formato automático de utilizar archivos compuestos.  Dado que un archivo compuesto se puede ver como “el sistema de archivos en un archivo”, los tipos de objeto individuales, como secuencia o almacenamiento, puede tener acceso sin necesidad de cargar el archivo completo.  Esto puede reducir considerablemente el tiempo que una aplicación necesita tener acceso a los objetos nuevos para la edición del usuario.  La actualización incremental, según el mismo concepto, ofrece ventajas similares.  En lugar de guardar el archivo completo solo para guardar los cambios realizados a un objeto, OLE guarda sólo la secuencia o el objeto de almacenamiento editado por el usuario.  
  
###  <a name="_core_file_access_modes"></a> Modos de acceso a archivos  
 El poder determinar cuando los cambios de los objetos en un archivo compuesto se confirman en el disco es otra ventaja de utilizar archivos compuestos.  El modo en que los archivos se realiza, tramitado o dirigen, determina cuando los cambios se confirman.  
  
-   El modo de transacción utiliza una operación de confirmación en dos fases para realizar cambios en objetos en un archivo compuesto, de esta manera conservando las antiguas y nuevas copias de documento disponible hasta que el usuario elija para guardar o deshacer los cambios.  
  
-   El modo directo incorpora cambios al documento como se crean, sin la capacidad de deshacer a ellos.  
  
 Para obtener más información acerca de los modos de acceso, vea *referencia\) del Programador*.  
  
###  <a name="_core_standardization"></a> Normalización  
 La estructura normalizada de archivos compuestos permite diferentes aplicaciones OLE para desplazarse por los archivos compuestos creados por la aplicación OLE sin conocimiento de la aplicación que creó realmente el archivo.  
  
###  <a name="_core_size_and_performance_considerations"></a> Tamaño y rendimiento Consideraciones  
 Debido a la complejidad de la estructura de almacenamiento de archivo compuesto y la capacidad de guardar datos, los archivos mediante este formato suelen ser más grandes que otros archivos utilizando almacenamiento no estructurado o “archivo plano”.  Si la aplicación con frecuencia cargue y guarde los archivos, utilizando los archivos compuestos puede hacer que el tamaño de archivo aumentar mucho más rápidamente que los archivos de noncompound.  Dado que los archivos compuestos pueden obtener grande, el tiempo de acceso de los archivos almacenados en y carga de discos también puede verse afectado, lo que da como resultado un acceso más lento en archivos.  
  
 El otro tema que afecta al rendimiento es fragmentación de archivo compuesto.  El tamaño de un archivo compuesto está determinado por la diferencia entre la primera y los sectores de disco pasados utilizados por el archivo.  Un archivo fragmentado puede contener muchas áreas de espacio disponible que no contienen datos, pero se cuentan al calcular el tamaño.  Durante la duración de un archivo compuesto, estas áreas son creadas por la inserción o eliminación de objetos de almacenamiento.  
  
##  <a name="_core_using_compound_files_format_for_your_data"></a> Utilizando el formato de archivos compuestos para los datos de El  
 Después correctamente de crear una aplicación que tiene una clase document derivada de `COleDocument`, asegúrese de que el constructor del documento principal llama `EnableCompoundFile`.  Cuando el asistente para aplicaciones crea aplicaciones contenedoras VIEJAS, esta llamada se inserta automáticamente.  
  
 En *la referencia\) del Programador*, vea [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034), [IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015), y [ILockBytes](http://msdn.microsoft.com/library/windows/desktop/aa379238).  
  
## Vea también  
 [Contenedores](../mfc/containers.md)   
 [Contenedores: Problemas de la interfaz de usuario](../mfc/containers-user-interface-issues.md)   
 [COleStreamFile Class](../mfc/reference/colestreamfile-class.md)   
 [COleDocument Class](../mfc/reference/coledocument-class.md)