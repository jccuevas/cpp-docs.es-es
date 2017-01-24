---
title: "CArchive Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CArchive"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CArchive class"
  - "data storage [C++], CArchive class"
  - "I/O [MFC], archiving objects"
  - "serialización [C++], CArchive class"
  - "storage [C++], CArchive class"
ms.assetid: 9e950d23-b874-456e-ae4b-fe00781a7699
caps.latest.revision: 21
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CArchive Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Permite guardar una red compleja de objetos en un formato binario permanente \(normalmente almacenamiento en disco\) que se conserva después de que se eliminen esos objetos.  
  
## Sintaxis  
  
```  
class CArchive  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CArchive::CArchive](../Topic/CArchive::CArchive.md)|Crea un objeto `CArchive`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CArchive::Abort](../Topic/CArchive::Abort.md)|Cerrar un archivo sin producir una excepción.|  
|[CArchive::Close](../Topic/CArchive::Close.md)|Vacía datos y desconexiones nos escrito de `CFile`.|  
|[CArchive::Flush](../Topic/CArchive::Flush.md)|Vacía datos nos tipo de búfer de archivo.|  
|[CArchive::GetFile](../Topic/CArchive::GetFile.md)|Obtiene el puntero de objeto de `CFile` para este archivo.|  
|[CArchive::GetObjectSchema](../Topic/CArchive::GetObjectSchema.md)|Nombre de la función de `Serialize` para determinar la versión del objeto que se está deserializando que.|  
|[CArchive::IsBufferEmpty](../Topic/CArchive::IsBufferEmpty.md)|determina si el búfer se ha vaciado durante Windows Sockets recibe proceso.|  
|[CArchive::IsLoading](../Topic/CArchive::IsLoading.md)|determina si el archivo está cargando.|  
|[CArchive::IsStoring](../Topic/CArchive::IsStoring.md)|determina si el archivo está almacenando.|  
|[CArchive::MapObject](../Topic/CArchive::MapObject.md)|Coloca los objetos del mapa que no están serializados en el archivo, pero que esté disponible para que los objetos secundarios se hace referencia.|  
|[CArchive::Read](../Topic/CArchive::Read.md)|lee bytes sin formato.|  
|[CArchive::ReadClass](../Topic/CArchive::ReadClass.md)|Lee una referencia de clase anteriormente almacenada con `WriteClass`.|  
|[CArchive::ReadObject](../Topic/CArchive::ReadObject.md)|Llama a la función de `Serialize` de un objeto para cargar.|  
|[CArchive::ReadString](../Topic/CArchive::ReadString.md)|Lee una línea de texto única.|  
|[CArchive::SerializeClass](../Topic/CArchive::SerializeClass.md)|Lee o escribe la referencia de clase al objeto de `CArchive` en función de la dirección de `CArchive`.|  
|[CArchive::SetLoadParams](../Topic/CArchive::SetLoadParams.md)|Establece el tamaño en el que la matriz de carga aumenta.  Debe llamar antes de cualquier objeto se carga o antes de llamar a `MapObject` o `ReadObject` .|  
|[CArchive::SetObjectSchema](../Topic/CArchive::SetObjectSchema.md)|Establece el esquema del objeto en el objeto de archivo.|  
|[CArchive::SetStoreParams](../Topic/CArchive::SetStoreParams.md)|Establece el tamaño de la tabla hash y el tamaño de bloque de asignación se utiliza para identificar objetos únicos durante el proceso de serialización.|  
|[CArchive::Write](../Topic/CArchive::Write.md)|escribe bytes sin formato.|  
|[CArchive::WriteClass](../Topic/CArchive::WriteClass.md)|escribe una referencia a `CRuntimeClass` a `CArchive`.|  
|[CArchive::WriteObject](../Topic/CArchive::WriteObject.md)|Llama a la función de `Serialize` de un objeto para almacenar.|  
|[CArchive::WriteString](../Topic/CArchive::WriteString.md)|Escribe una línea de texto única.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CArchive::operator \<\<](../Topic/CArchive::operator%20%3C%3C.md)|Almacena objetos y tipos primitivos al archivo.|  
|[CArchive::operator \>\>](../Topic/CArchive::operator%20%3E%3E.md)|Objetos y tipos primitivos de las cargas de archivos.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CArchive::m\_pDocument](../Topic/CArchive::m_pDocument.md)||  
  
## Comentarios  
 `CArchive` no tiene una clase base.  
  
 Puede cargar posteriormente los objetos de almacenamiento persistente, reconstituyéndolos en memoria.  Este proceso para crear datos persistentes se denomina “serialización.”  
  
 Puede pensar en un objeto de archivo como una clase de secuencia binaria.  Como una secuencia de entrada y salida, un archivo está asociado a un archivo y permite escribir y la lectura de datos almacenado en búfer a y de almacenamiento.  Una entrada transmitir secuencias de procesos de caracteres ASCII, pero un datos binarios de objeto de los procesos del archivo en formato eficaz, nonredundant.  
  
 Debe crear un objeto de [Archivo C](../../mfc/reference/cfile-class.md) antes de crear un objeto de `CArchive` .  Además, debe asegurarse de que la carga y el estado almacenado de archivo es compatibles con el modo de apertura de archivo.  Se limita a un archivo activo por el archivo.  
  
 Cuando se crea un objeto de `CArchive` , lo asocia a un objeto de la clase `CFile` \(o una clase derivada\) que representa un archivo abierto.  También especifica si el archivo se utilizará para cargar o guardar.  Un objeto de `CArchive` puede procesar no solo los tipos primitivos pero también los objetos de [CObject](../../mfc/reference/cobject-class.md)\- clases derivadas diseñadas para la serialización.  Una clase serializable tiene normalmente una función miembro de `Serialize` , y suele utilizar macros de [DECLARE\_SERIAL](../Topic/DECLARE_SERIAL.md) y de [IMPLEMENT\_SERIAL](../Topic/IMPLEMENT_SERIAL.md) , como se describe en clase `CObject`.  
  
 Los operadores sobrecargados de extracción \(**\>\>**\) y de inserción \(**\<\<**\) son las interfaces de programación adecuadas de archivo que admiten los tipos primitivos y `CObject`\- clases derivadas.  
  
 `CArchive` también admite la programación con las clases [CSocket](../../mfc/reference/csocket-class.md) y [CSocketFile](../../mfc/reference/csocketfile-class.md)de Windows Sockets de MFC.  La función miembro de [IsBufferEmpty](../Topic/CArchive::IsBufferEmpty.md) admite ese uso.  
  
 Para obtener más información sobre `CArchive`, vea los artículos [serialización](../../mfc/serialization-in-mfc.md) y [Windows Sockets: Mediante sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
## Jerarquía de herencia  
 `CArchive`  
  
## Requisitos  
 **encabezado:** afx.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CFile Class](../../mfc/reference/cfile-class.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [CSocket Class](../../mfc/reference/csocket-class.md)   
 [CSocketFile Class](../../mfc/reference/csocketfile-class.md)