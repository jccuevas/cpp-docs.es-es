---
title: "Serializaci&#243;n en MFC | Microsoft Docs"
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
  - "excluir serialización"
  - "clases de colección, serialización"
  - "MFC, serialización"
  - "serialización [C++], omitir"
  - "serialización [C++], MFC"
ms.assetid: fb596a18-4522-47e0-96e0-192732d24c12
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Serializaci&#243;n en MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica el mecanismo de serialización proporcionado en la biblioteca Microsoft Foundation Class \(MFC\) para permitir que los objetos se conserven entre el programa.  
  
 La serialización es el proceso de escritura o lectura un objeto a o desde un medio de almacenamiento persistente como un archivo de disco.  La serialización es ideal en situaciones donde se desea mantener el estado de datos estructurados \(como clases o estructuras de C\+\+\) durante o después de la ejecución de un programa.  Mediante los objetos de serialización proporcionados por MFC permite que aparezca de una manera estándar y coherente, aliviando al usuario de la necesidad de realizar operaciones de archivo a mano.  
  
 Compatibilidad integrada de MFC para la serialización en la clase `CObject`.  Así, todas las clases derivadas de `CObject` pueden aprovecharse de protocolo de serialización de `CObject` .  
  
 La idea básica de la serialización es de que un objeto puede escribir su estado actual, indicado normalmente por el valor de sus variables miembro, el almacenamiento persistente.  Después, el objeto puede reconstruirla leyendo, o deserializar, el estado del objeto del almacenamiento.  La serialización controla todos los detalles de los punteros de objeto y referencias circulares a los objetos que se usan cuando se serializa un objeto.  Un punto clave es que el propio objeto es responsable de leer y escribir su propio estado.  Por tanto, para que una clase es serializable, debe implementar las operaciones básicas de serialización.  Como se muestra en el grupo de Serialización de casos, resulta fácil agregar esta funcionalidad a una clase.  
  
 MFC utiliza un objeto de clase de `CArchive` como un intermediario entre el objeto que se serializarán y medio de almacenamiento.  Este objeto se asocia siempre a un objeto de `CFile` , de que recopila la información necesaria para la serialización, incluido el nombre de archivo y de si la operación solicitada es una lectura o una escritura.  El objeto que realiza una operación de serialización puede utilizar el objeto de `CArchive` sin tener en cuenta la naturaleza del medio de almacenamiento.  
  
 Un objeto de `CArchive` utiliza operadores sobrecargados de inserción \(**\<\<**\) y extracción \(**\>\>**\) para realizar operaciones de escritura y lectura.  Para obtener más información, vea [Almacenar y cargando CObjects mediante un archivo](../mfc/storing-and-loading-cobjects-via-an-archive.md) en el artículo Serialización: Serialización de un objeto.  
  
> [!NOTE]
>  No confunda la clase de `CArchive` con clases de uso general iostream, para el texto con formato.  La clase de `CArchive` es para los objetos serializados formato binario.  
  
 Si lo desea, puede omitir la serialización de MFC para crear dispone del mecanismo para el almacenamiento de datos persistente.  Deberá reemplazar el miembro de clase funciona esa serialización iniciado en el comando de usuario.  Vea la explicación de [Nota técnica 22](../mfc/tn022-standard-commands-implementation.md) de los comandos de `ID_FILE_OPEN`, standard de **ID\_FILE\_SAVE**, y de **ID\_FILE\_SAVE\_AS** .  
  
 Los casos siguientes se tratan los dos tareas principales necesarios para la serialización:  
  
-   [Serialización: Crear una clase Serializable](../mfc/serialization-making-a-serializable-class.md)  
  
-   [Serialización: Serialización de un objeto](../mfc/serialization-serializing-an-object.md)  
  
 El artículo [Serialización: Serialización en la base de datos Entrada\- generada](../mfc/serialization-serialization-vs-database-input-output.md) describe cuando la serialización es una técnica adecuada de entrada\/salida en aplicaciones de base de datos.  
  
## Vea también  
 [Conceptos](../mfc/mfc-concepts.md)   
 [Temas generales de MFC](../mfc/general-mfc-topics.md)   
 [CArchive Class](../mfc/reference/carchive-class.md)   
 [CObject Class](../mfc/reference/cobject-class.md)   
 [CDocument Class](../mfc/reference/cdocument-class.md)   
 [CFile Class](../mfc/reference/cfile-class.md)